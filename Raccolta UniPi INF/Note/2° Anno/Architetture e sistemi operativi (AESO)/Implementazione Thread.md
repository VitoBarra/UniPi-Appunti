---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Implementazione Thread
---

# Kernel Multi-Thread

## Creazione

1. Alloca il per-thread state quindi TCB e Stack
2. inizializza il per-thread state:
    - invece di chiamare direttamente la funzione passata al thread con i suoi argomenti viene prima chiamata un altra funzione stub che si occuperà di fare da wraper per la funzione essenzialmente qualcosa che contiene la funzione che va chiamata ma che in caso di return di questa poi riesca a chiarem pthread_exit();

        ```c
        void stub(void (*func)(int), int arg) {
         (*func)(arg); // Execute the function func()
         thread_exit(0); // If func() does not call exit, call it here.
         }
        ```

    - viene messo sullo stack un record d attivazione “Dummy” per facilitare lo switch di contesto da un thread ad un altro
3. mettere il TCB in stato Ready e spostarlo nella ReadyListv

## Cancellazione di Thread

il thread una volta chiamato l exit deve essere spostato nella FinishedList dove verra mantenuto Il suo TCB con il risultato del thread. una volta consumato quel dato si puo procedere a fare il free del TCB.

Della deallocazione se ne occuperà un altro thread farlo fare al thread stesso porta a problemi perché potrebbe essere interrotto mentre la deallocazione non è completata, per esempio se non esiste più lo stack e il TCB non è stato ancora deallocato e arriva un interruzione

## Cambio di contesto

il cambio di contesto consiste nel salvare lo stato del thread metterlo in pausa e riprendere l esecuzione di un altro thread

può succedere in due modi

### Volontario

con la chiamata da parte del thread  ad Thread_yield che rilascia il processore. mentre si fa questa operazione si devono mascherare le interruzioni


>[!info] **Why is it necessary to turn off interrupts during thread switch?**
Our implementation of thread_yield defers any interrupts that might occur during the procedure, until the yield is complete. This might seem unnecessary: after all, even if the thread context switch is interrupted, the state of the switch will be saved onto the stack. Eventually the kernel will re-schedule the thread, restore its state, and complete the thread switch.
However, a subtle inconsistency might arise. Suppose a low priority thread (e.g., the idle thread) is about to voluntarily switch to a high priority thread. It pulls the high priority thread off the ready list, and at that precise moment, an interrupt occurs. Supppose the interrupt moves a medium priority thread from WAITING to READY. Since it appears that the processor is still running the low priority thread, the interrupt handler immediately switches to the new thread. The high priority thread is in limbo! It is ready to run, but unable to do so until the low priority thread is re-scheduled. And that may not happen for a long time.
Of course, this sequence of events would not occur very often, but when it does, it would be difficult to locate
or debug.

per fare l effettivo cambio da un thread al altro c è bisogno di una funzione che opera direttamente sullo stack attivo.

```c
// We enter as oldThread, but we return as newThread.
// Returns with newThread’s registers and stack.
 void thread_switch(oldThreadTCB, newThreadTCB)
{
	 pushad;                  // Push general register values onto the old stack.
	 oldThreadTCB->sp = %esp; // Save the old thread’s stack pointer.
	 %esp = newThreadTCB->sp; // Switch to the new stack.
	 popad;                   // Pop register values from the new stack.
	 return;
 }
```

questa funzione prima salva i registri sullo stack corrente il cui puntatore viene salvato sul TCB del primo Thread successivamente carina il nuovo stack presente sul TCB del nuovo thread che deve andare in esecuzione e carica i registri salvati su quel nuovo stack nei registri del processore

```c
void thread_yield()
{
	 TCB *chosenTCB, *finishedTCB;
	 // Prevent an interrupt from stopping us in the middle of a switch.
	 disableInterrupts();
	 // Choose another TCB from the ready list.
	 chosenTCB = readyList.getNextThread();
	 if (chosenTCB == NULL) {
	 // Nothing else to run, so go back to running the original thread.
	 } else {
	 // Move running thread onto the ready list.
	 runningThread->state = ready;
	 readyList.add(runningThread);
	 thread_switch(runningThread, chosenTCB); // Switch to the new thread.
	 runningThread->state = running;
	 }
	 // Delete any threads on the finished list.
	 while ((finishedTCB = finishedList->getNextThread()) != NULL) {
	 delete finishedTCB->stack;
	 delete finishedTCB;
	 }
	 enableInterrupts();
}
```

```c
// thread_create must put a dummy frame at the top of its stack:
// the return PC and space for pushad to have stored a copy of the registers.
// This way, when someone switches to a newly created thread,
// the last two lines of thread_switch work correctly.
void thread_dummySwitchFrame(newThread)
{
	 *(tcb->sp) = stub; // Return to the beginning of stub.
	 tcb->sp--;
	 tcb->sp -= SizeOfPopad;
}
```

### Involontario

con un interrupt o un eccezione

 per eseguire lo switch di contesto si fanno passi simili al cambio di processo :

1. salva lo stato: salva i registri del thread
2. Lancia l handler del kernel: non c è bisogno di cabiare modalita perche siamo gia nel kenel e si puo usare lo stack corrente del kernel per la gestione del handler
3. ripresinare lo stato:  stato di un altro thread Ready ti run assumendo che sia stato interrotto

differenze con il User-mode transfer:

- non c è bisogno di cambiare modalita
- l handler puo riprendere qualsiasi processo assumedo che sia stato sospeso in precendenza

# Kernel Treades e Single-Threaded processi user

la lista dei Ready puo contetenere  sia PCB che TCB  siccome questi entrambi rappresentano un singolo flusso di esecuzione e puo quindi trattarli in modo uguale. in entrambi i casi lo stato deve essere salvato prima

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3 6.png]]

c è un unica differenza nella gestione delle interruzioni. Nel caso il processo sia già in modalità kernel (controllando il bit Eflag) utilizza lo stack già correntemente in uso quindi non salva lo stack pointer e alla fine del esecuzione del handler controlla il bit salvato sullo stack e il corrente se sono uguali ritorna sullo stack corrente e continua L esecuzione. Nel gli altri casi fa le normale procedure di cambio processo

# implementazione Process Multy-Threaded

I thread vengono generati chiamando delle syscall delegando quindi la creazione di nuovi thread al kernel.

Questo crea un TCB nel kernel per-thread e uno stack kernel per le interruzioni. Mette poi nella ready list il TCB come qualsiasi altro thread

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 1 1.png]]

Tutte le operazioni su thread quali thread join yield e exit funzionano esattamente come i thread kernel

# Processi Multi-Thread User-Level


# Without Kernel Support

Si possono creare thread ad user-level chiamati green-Thread ricreando le stesse strutture dati che userebbe il sistema operativo ad user-level (TCBs, finished list, ready list etc.). Quindi queste strutture dati sarebbero nello spazio di indirizzamento del processo che ne fa utilizzo.

- **Pro:**
    - Incrementa la portabilità non dipendendo da uno specifico sistema operativo
- **contro:**

    Al kernel i programmi con thread user-level appaino come normali processi e lavora quindi come tale. Il che porta a:

    - Alla sospensione di un singolo thread si sospende l intero processo (es: in caso di IO)
    - Non permette di usare a proprio vantaggio L avere più processori

### User-Level Thread con periclasio

Si posso implementare utilizzando le [[Upcalls]] fornite dal sistema operativo. Per fare periclasio di user-thread di un processo  P vanno fatti i seguenti passi:

1. La libreria thread registra un handler di segnarli con timer
2. Quando arriva l interruzione del timer L hardware salva i registri di P E lancia L handler kernel
3. Alla fine del handler invece di riprendere L esecuzione del processo copia i registri messi da parte del processo P nello sack dei segnali
4. Il kernel riprende P nel Handler del segnare User-Level
5. L handler copia il registri salvati sul signal stack nel TCB di quel processo
6. L handler selezione un altro thread da riavviare e riattiva il signal handler

## With Kernel Support