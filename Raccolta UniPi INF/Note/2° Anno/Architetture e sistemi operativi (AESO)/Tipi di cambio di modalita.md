# Tipi di cambio di modalita

con il dual-mode operation ora c è bisogno di transitare da una modalita al altra  anche migliaglia di volte al secodo percio devono essere volici e sicure.

# da User a Kernel Mode

c è un trasferimento di contensto in questi casi:

## interruzioni:

 sono segnali asincroni che vengono al processore che vengono mandati da qualche evento esterno. di solito sono generate da dispositivi di I/O  che chiamano un interuzione ogni volta che si deve fare un operazione se quei dispositivi. il processore completa o mette in pausa quello che stavo eseguendo, slva lo stato corrente del processo e manda in esecuzione l hadler di quella specifica interruzione.
un altro modo per gestire questo dispositivi è il polling essenzialmente il kernel loopa su tutti i dispositivi finche uno di essi non ha una richiesta che deve essere gestita

## Processor exceptoion:

è un evento hardwere causato dal user, quando viene sollevata l accezione il processore termina l istruzione che stava eseguendo , salva lo stato del processo e chiama un hendler del eccezzione. un esempop di questo è un processo che tenta di dividere per 0. In caso di multiplrocessore la sollevazione di un eccezione stoppa solo il processo triggerato, gli altri vengono intrettortti dal kernel.

<aside>
💡 si pososno usare anche per casi benefici infatti questa tipo di ecezione si utilizza per implementare breackpoint e la possibilita di esegurei passo dopo passo il codice.
infatti quando si setta un break point l istruzione  dove è stato fatto viene sostituito con una trap (istruzione che fa lo switch di contesto da user a kernel) e poi viene ripristinata l istruzione corretta quando l esecuzione sara arrivata a quel punto . successivamente il kernel passa il controllo al debugger

</aside>

[[Untitled 33.png]]

## Chiamate di sistema:

essenzialmente rutine predefinite che possono essere chiamate dal un processo ma causano il cambio di contesto siccome richiedono operazioni che solo il kernel puo svoltegere per loro. è importante che siano routine predefinite cosi che il processo in user mode non possa accedere ad un punto albritario del kernel

# da Kernel ad user

### nuovi Processi

il kernel fa partire un nuovo proccesso copiando in memoria il programma e, impostando il Program Counter alla prima istruzione e settando il puntatore dello base di stack allo user stack e fa lo switch di contesto

### Riprendere dopo un interruzione un eccezzione di precessore o una syscal

dopo l esecuzione degl hendler specifico il kernel ripristina lo stato precedente e il program counter poi esegue il cambio di contesto

### Cambiando da un processo ad un altro

nei casi in cui un processo viene interroto e ne viene un altro il kernel deve salvare lo stato nel PCB (proces control block) e quando quel processo vera ripreso quello stato dovra essere ripristina nel processore e poi eseguito il cambio di contesto

### User-Level upcall

un mecanismo che permette ad i prgrammi di gestire delle notifiche asincrone come le interruzioni ma ad user level quindi provenienti dal kernel diretti verso un processo in user-level



---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
