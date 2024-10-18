---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Thread Pool
---


## Che problema affronta

I thread hanno un overhead di gestione (interazione con OS ) e e un cost in termini di risorse sulla memoria siccome ogni thread ha il suo stack privato e c è  più “stress” sul [[Garbage Collector]]

questo può essere un problema di fatto si potrebbe arrivare a pagare più overhead del vantaggio che si ottiene usando più thread.

![[UniPi-Appunti/Studi/Triennale Informatica/Reti/Media/Untitled.png]]


>[!info]
per evitare questo i [[Sistemi Operativi]] di solito limitano il numero di Thread per programma



![[UniPi-Appunti/Studi/Triennale Informatica/Reti/Media/Untitled 1.png]]

numero di thread limitato dal livello di capacità di [[Implementazione Thread#Kernel Multi-Thread|kernel thread]]

“JAVA break” se si usano più thread di quelli supportati dal [[Sistemi Operativi|Sistema Operativo]]

# Thread Pool
nel caso ci siano molte task e si vorrebbe aprire un thread per task per non pagare l overhead si può utilizzare una ThreadPool ovvero un set di thread che possono essere riutilizzati.

le ThreadPool sono di più tipi e deferisco sulle politiche di gestione

### Politiche Da scegliere

- _Mantenimento_: dei thread
    - es.  il numero di thread può variare, come lo fa
- _Attivazione_: di quali thread
    - es. scelta del thread a cui dare il nuovo task, quando mandarlo in esecuzione (quindi può essere ritardata rispetto al arrivo)
- _Gestione_: cosa succede quando i task arrivano (sono impostabili alla creazione del task) : (DA VEDERE)
	- AbortPolicy : politica di default, consiste nel sollevare __RejectedExecutionException__ 
	-  DiscardPolicy, DiscardOldestPolicy, CallerRunsPolicy: altre politiche predefinite

![[UniPi-Appunti/Studi/Triennale Informatica/Reti/Media/Untitled 2.png]]
## Chiusura Thread pool
la thradPool può essere chiusa in due modi
1. __Graduale__: cerca di finire i task che in esecuzione e in coda e non accetta i nuovi task che arrivano
	- _ShutDown_(): inizia la chiusura e solleva l eccezione [[Java RejectionExecutionException|RejectionExecutionException]] al arrivo di nuovi task
	- _isShutdown_(): da true se è stato invocato precedentemente _Shutdown_()
	- _isTermined_(): controlla che i task sono terminati 
	- _awaitTermination_(long timeout, TimeUnit unit): si blocca finche finche i task non finiscono o finisce il timer, ritorna true se i task sono finiti false se è scaduto il timer 
2. __instantanea__: chiude la threadpool senza aspettare che i task in coda vadano in esecuzione
	+ _ShutDownNow_(): non fa accettare alla pool nuovi task ed elimina quelli in coda restituendoli con una lista in uscita 
		+ non garantisce la terminazione immediata perché cerca di finire i task in esecuzione e se un thread si è bloccato lo shutDown non viene completato  

## Scegliere il numero di thread nel threadPool
- Se *CPU-Bound*: conviene avere il numero di thread pari al nume di core 
- se *IO-Bound*: ha senso avere più thread che core siccome alcuni potrebbero andare in attesa 


>[!note]
>Per la gestione pratica delle threadPool in [[java]] si utilizzano gli [[Executor]]


