---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# implementare sistemi sicuri di cambio modalità
---
	

Per poter implementare di cambi di modalità sicuri il sistema deve provvedere almeno queste cose

- numeri d accesso al kernel limitati: va limitata la possibilità al utente di saltare in parti arbitrarie del kernel ma deve passare necessariamente per i punti d accesso definite dal kernel stresso cosi che da permettere i dovuti controlli
- [[Transazioni|transizione atomiche]] tra le modalità: la transizione tra le modalità kernel e user ma in generale tra una modalità e l altra deve avvenire in modo atomico, quindi program counter, stack e i sistemi di protezione memoria vengono cambiati in una unica operazione
- esecuzione trasparenti e restartable : un programma non deve accorgersi di un interruzione che è stata ricevuta appunto deve essere trasparente. il processo utente che ha subito l interruzione deve essere riprendibili esattamente da dove era stato lasciato. questo si ottiene salvando lo stato al momento del interruzione e ricaricandolo al momento della ripresa.

## Interrupt Vector Table

il vettore della interruzioni sono una tabella di puntatori a procedure, queste procedure sono gli Chandler delle intrusioni implementate dal kernel.

sono raggiunte dal kernel grazie ad un registro che punta al indirizzo del array.

![[Untitled 34.png]]

 il formato del vettore di interruzioni è specifico per ogni processore.



## Interrupt Stack

 l stack delle interruzioni è una zona di memoria del kernel che serve a gestire la interruzioni che arrivano ad i vari processi.

nello specifico quando un processo subisce un interruzione il suo stato viene pushato sul stack di interruzione e una volta che l handler è terminato quello stato viene poppato.

nel caso del syscall viene anche incrementato di uno il PC cosi da non rieseguire la syscall.

questo stack è in memoria kernel e non user per due ragioni:

- affidabilità: il processo user potrebbe avere un indirizzo sbagliato ma gli handler devono comunque funzionare
- sicurezza: in caso di multiprocessore  gli altri thread potrebbero cambiare l indirizzo di ritorno dei un handler permettendo cosi al programma user di andare in un punto arbitrario del kernel.

in caso di multiprocessore inizialmente ogni processore deve avare uno stack di interruzione personale cosi da poter gestire più syscall su più processori contemporaneamente.

## Two stack per process

nei sistemi operativi odierni il kernel due stack al avvio del processo.

- user: per l user code
- kernel: per il kernel code

durante l esecuzione del programma il registro hardware  dello stack di interruzione ha un puntatore allo stack kernel. questo rende facile switchare da un processo che deve aspettare (ad esempio l’ I/O) ad uno che invece può girare.

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 1 16.png]]

## Interrupt Masking

le interruzioni possono arrivare in qualsiasi momento ma avvolte queste non dovrebbero essere gestite al istante perché potrebbe creare problemi, per esempio durante la gestione di un altra interruzione o durante l esecuzione dello scheduler. quindi esistono istruzioni per disabilita e riabilitare le interruzioni queste istruzioni sono privilegiate e quindi non possono essere eseguite in user mode

le interruzioni che arrivano mentre sono disabilitate non vengono perse ma messe in un buffer che le accumula e le fa gestire quando è sicuro farlo.
