# implementare sistemi sicuri di cambio modalita

Per poter implementare di cambi di modalità sicuri il sistema deve provvedere almeno queste cose

- numeri d accesso al kernel limitati: va limitata la posibilita al utente di saltare in parti arbitrarie del kernel ma deve passare necessariamente per i punti d accesso definite dal kernel stresso cosi che da permettere i dovuti controlli
- transizione atomiche tra le modalita: la transizione tra le modalita kernel e user ma in generale tra una modalita e l altra deve avvenire in modo atomico, quindi program counter, stack e i sistemi di protazione memoria vengono cambiati in una unica operazione
- esecuzione trasparenti e restartable : un programma non deve accorgersi di un interruzione che è stata ricevuta appunto deve essere trasparente. il processo utente che ha subito l interruzione deve essere riprendibili esattamente da dove era stato lasciato. questo si ottiene salvando lo stato al momento del interruzione e ricaricandolo al momento della ripresa.

## Interrupt Vector Table

il vettore della interuzioni sono una tabella di puntatori a procedure, queste procedure sono gli handler delle intruzioni implementate dal kernel.

sono ragiutne dal kernel grazie ad un registro che punta al indirizzo del array.

[[Untitled 34.png]]

 il formato del vottore di interruzioni è specifico per ogni processore.



## Interrupt Stack

 l stack delle interruzioni è una zona di momoria del kernel che serve a gestire la interruzioni che arrivano ad i vari processi.

nello specifico quando un processo subisce un intruzione il suo stato viene pushato sul stack di interruzione e una volta che l handle è terminato quello stato viene poppato.

nel caso dell syscall viene anche incrementato di uno il PC cosi da non rieseguire la syscall.

questo stack è in memoria kernel e non user per due ragioni:

- affidabilita: il processo user protrebbe avere un indirizzo sbagliato ma gli handler devono comunque funzionare
- sicurezza: in caso di multiprocessore  gli altri tread potrebbero cambiare l indirizzo di ritorno dei un hendler permettendo cosi al programma user di andare in un punto arbitrario del kernel.

in caso di multiprocessore inizialmente ogni processore deve avare uno stack di interruzione personale cosi da poter gestire piu syscall su piu processorei contemporaneamente.

## Two stack per process

nei sistemi operativi odierni il kernel due stack al avvio del processo.

- user: per l user code
- kernel: per il kernel code

duretante l esecuzione del programma il registro hardware  dello stack di interruzine ha un puntatore allo stack kernel. questo rende facile switchare da un processo che deve aspettare (ad esempio l’ I/O) ad uno che invece puo girare.

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 16.png]]

## Interrupt Masking

le interruzioni possono arrivare in qualsiasi momento ma avvolte queste non dovrebbero essere gestite al istante perche potrebbe creare problemi, per esempio duraten la gestione di un altra interruzione o durante l esecuzione dello scheduler. quindi esistono istruzioni per disabilita e riabilitare le inrettuzioni questre istruzioni sono privilegiate e quindi non possono essere eseguite in user mode

le interuzioni che arrivano mentre sono disabilitate non vengono perse ma messe in un buffer che le accumula e le fa gestire quando è sicuro farlo.



---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
