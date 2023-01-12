---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Astrazione Thread
---
i thread sono sequenze logiche di istruzioni in al interno di un processo su ciò non si possono fare assunzioni sul quando verrà eseguito, e quindi non si possono fare assunzioni sulle velocita relative a gli altri thread

### A cosa servono

permettono di

- parallelizzare l esecuzione di più task di un singolo processo in più flussi logici
- ridurre le attese attive facendo eseguire altri thread mentre uno è in attesa
- organizzare il programma in flussi logici indipendenti che possono comunicare

# Organizzazione dei thread

il sistema operativo può avviare sospendere e riprendere thread e tutto ciò è trasparente al thread stesso, dalla sua prospettiva il sistema operativo gli sta dando un processore virtuale in cui esegue solo lui, cosa ovviamente non vera siccome  solitamente i pressorie disponibili sono meno dei thread da eseguire.

per fare le operazioni sui thread si utilizzano i seguenti dati:

## Thread Control Block (TCB)

il Thread Control Block (TCB) una struttura per rappresentare lo stato del thread, il sistema operativo ne crea uno per ogni thread e contiene dati di due tipi:

### 1. Stato della computazione

- puntatore a Stack: ogni thread a un suo stack per le chiamate, un normale stack dove ci saranno i blocchi d attivazione
- copia dei registri: possono essere salvati o direttamente in una zona di memoria del TCB o pusahti sullo stack

### 2. Metadati

- Metadati: come Thread ID, stato del thread, priorità

## Shared State

Lo shared State sono tutto quello che i thread condividono nello stesso processo o nel kernel stesso, di conseguenza c è ne uno per processo e al suo interno troviamo

- le variabili globali
- lo heap
- il codice

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 26.png]]

## Ciclo vitale dei thread

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 15.png]]

- INIT. Thread creation puts a thread into its INIT state and allocates and initializes perthread data structures. Once that is done, thread creation code puts the thread into the READY state by adding the thread to the ready list. The ready list is the set of runnable
threads that are waiting their turn to use a processor. In practice, as discussed in
Chapter 7, the ready list is not in fact a “list”; the operating system typically uses a more
sophisticated data structure to keep track of runnable threads, such as a priority queue.
Nevertheless, following convention, we will continue to refer to it as the ready list.
- READY. A thread in the READY state is available to be run but is not currently running. Its
TCB is on the ready list, and the values of its registers are stored in its TCB. At any time,
the scheduler can cause a thread to transition from READY to RUNNING by copying its
register values from its TCB to a processor’s registers.
- RUNNING. A thread in the RUNNING state is running on a processor. At this time, its
register values are stored on the processor rather than in the TCB. A RUNNING thread can
transition to the READY state in two ways:
    - The scheduler can preempt a running thread and move it to the READY state by: (1)
    saving the thread’s registers to its TCB and (2) switching the processor to run the next
    thread on the ready list.
    - A running thread can voluntarily relinquish the processor and go from RUNNING to
    READY by calling yield (e.g., thread_yield in the thread library).

the TCB is stored on the waiting list of some synchronization variable associated with the
    Notice that a thread can transition from READY to RUNNING and back many times. Since
    the operating system saves and restores the thread’s registers exactly, only the speed of
    the thread’s execution is affected by these transitions.


>[!warning]
> By convention in this book, a thread that is RUNNING is not on the ready list;the ready list is for READY and not RUNNING threads. However, some operating systems,such as Linux, use a different convention, where the RUNNING thread is whichever threadis at the front of the ready list. Either convention is equivalent as long as it used consistently.


- WAITING. A thread in the WAITING state is waiting for some event. Whereas the
scheduler can move a thread in the READY state to the RUNNING state, a thread in the
WAITING state cannot run until some action by another thread moves it from WAITING to
READY.
The threadHello program in Figure 4.6 provides an example of a WAITING thread. After
creating its children threads, the main thread must wait for them to complete, by calling
thread_join once for each child. If the specific child thread is not yet done at the time of the
join, the main thread goes from RUNNING to WAITING until the child thread exits.
While a thread waits for an event, it cannot make progress; therefore, it is not useful to run
it. Rather than continuing to run the thread or storing the TCB on the scheduler’s ready list,
event. When the required event occurs, the operating system moves the TCB from the
synchronization variable’s waiting list to the scheduler’s ready list, transitioning the thread
from WAITING to READY. We describe synchronization variables in Chapter 5.
- FINISHED. A thread in the FINISHED state never runs again. The system can free some
or all of its state for other uses, though it may keep some remnants of the thread in the
FINISHED state for a time by putting the TCB on a finished list. For example, the
thread_exit call lets a thread pass its exit value to its parent thread via thread_join.
Eventually, when a thread’s state is no longer needed (e.g., after its exit value has been
read by the join call), the system can delete and reclaim the thread’s state.

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 9.png]]
