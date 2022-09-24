---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Tipi di cambio di modalita
---
con il dual-mode operation ora c è bisogno di transitare da una modalità al altra  anche miglia glia di volte al secondo perciò devono essere veloci e sicure.

# da User a Kernel Mode

c è un cambio di modalità nei seguenti casi:

## interruzioni:

 sono segnali asincroni che vengono al processore che vengono mandati da qualche evento esterno. di solito sono generate da dispositivi di I/O  che chiamano un interruzione ogni volta che si deve fare un operazione se quei dispositivi. il processore completa o mette in pausa quello che stavo eseguendo, salva lo stato corrente del processo e manda in esecuzione l handler di quella specifica interruzione.
un altro modo per gestire questo dispositivi è il polling essenzialmente il kernel loopa su tutti i dispositivi finche uno di essi non ha una richiesta che deve essere gestita

## Processor exceptoion:

è un evento hardware causato dal user, quando viene sollevata l accezione il processore termina l istruzione che stava eseguendo , salva lo stato del processo e chiama un handler del eccezione. un esempio di questo è un processo che tenta di dividere per 0. In caso di multiprocessore la sollevazione di un eccezione stoppa solo il processo triggerato, gli altri vengono interrotti dal kernel.


>[!info]
>si possono usare anche per casi benefici infatti questa tipo di eccezione si utilizza per implementare breackpoint e la possibilità di eseguirei passo dopo passo il codice.
infatti quando si setta un break point l istruzione  dove è stato fatto viene sostituito con una trap (istruzione che fa lo switch di contesto da user a kernel) e poi viene ripristinata l istruzione corretta quando l esecuzione sarà arrivata a quel punto . successivamente il kernel passa il controllo al Debugger



![[Untitled 33.png]]

## Chiamate di sistema:

essenzialmente rutine predefinite che possono essere chiamate dal un processo ma causano il cambio di contesto siccome richiedono operazioni che solo il kernel può svolgere per loro. è importante che siano routine predefinite cosi che il processo in user mode non possa accedere ad un punto arbitrario del kernel

# da Kernel ad user

### nuovi Processi

il kernel fa partire un nuovo processo copiando in memoria il programma e, impostando il Program Counter alla prima istruzione e settando il puntatore dello base di stack allo user stack e fa lo switch di contesto

### Riprendere dopo un interruzione un eccezione di precessore o una syscal

dopo l esecuzione del handler specifico il kernel ripristina lo stato precedente e il program counter poi esegue il cambio di contesto

### Cambiando da un processo ad un altro

nei casi in cui un processo viene interroto e ne viene un altro il kernel deve salvare lo stato nel PCB (proces control block) e quando quel processo vera ripreso quello stato dovra essere ripristina nel processore e poi eseguito il cambio di contesto

### User-Level upcall

un meccanismo che permette ad i programmi di gestire delle notifiche asincrone come le interruzioni ma ad user level quindi provenienti dal kernel diretti verso un processo in user-level
