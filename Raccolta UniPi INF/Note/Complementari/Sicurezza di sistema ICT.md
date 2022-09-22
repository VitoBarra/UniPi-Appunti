# Sicurezza di sistema ICT

### Le parole chiave:

### Confidenzialità

Solo chi ha il diritto di leggere una certa informazione può farlo. La specifica (regola) di sicurezza deve garantire ciò.

### Integrità

Solo chi ha il diritto di aggiornare una certa informazione può farlo.

Queste prime proprietà ci dicono che l’implementazione di un sistema rispetta le specifiche date dalla politica di sicurezza.

### Disponibilità

chi ha un diritto e vuole esercitarlo, deve poterlo fare in un tempo finito. Meglio se ragionevolmente breve.

La terza proprietà impone un vincolo temporale per cui il sistema deve garantire che le richieste siano soddisfatte in un tempo finito; proprietà estremamente complessa che imoone anche vincoli su risorse disponibili.

## Proprietà di sicurezza derivate

- **Tracciabilità:** individuare chi ha invocato un’operazione
- **Accountability:** Addebitare l’uso delle risorse
- **Auditability:** Verificare l’efficacia dei meccanismi di enforcement di una politica (come viene realizzata)
- **Forensics:** Provare che certe azioni hanno avuto luogo
- **Privacy/GDPR:** Chi/Come/Se può usare informazioni personali

# Politica di sicurezza

## Cosa sono?

Sono una serie di regole definite dal proprietario del sistema o del processo aziendale per decidere gli utenti che possono invocare un’operazione e quando possono farlo.

Esistono diverse categorie, risultato di due scelte indipendenti (ortogonali)

## Prima scelta: Come si descrive?

### Default allow

La politica definisce le operazioni vietate

### Default deny

La politica definisce le operazioni permesse

## Seconda scelta: Quali sono i vincoli per il proprietario di sistema?

### Discretionary Access Control

Decide il proprietario → tipica scelta del mondo commerciale

### Mandatory Access Control

Esistono vincoli globali a tutto il sistema che nemmeno il proprietario può violare, tipico del mondo militare

Ha una serie di caratteristiche che non permettono la divulgazione delle informazioni a soggetti non autorizzati.

Ci muoviamo per livelli, che possono essere assegnati dall’owner e servono per accessibility alle informazioni. Il check del livello avviene per confronto di livello di clearance.

Livello soggetto = quanto ci fidiamo

Livello oggetto = quanto è importante

# 2° Lecture (21/09/22)

## Seconda Scelta: Soggetti e Oggetti

- Una definizione rigorosa della politica modella risorse condivise come **oggetti** ed utenti come **soggetti** che su di esse operano
- I soggetti invocano le operazioni definite dagli oggetti
- Se un oggetto invoca le operazioni definite da altri oggetti allora diventa esso stesso un soggetto
- Soggetto/oggetto dipende dal livello di implementazione

### Soggetto

Utente,applicazione,programma,processo,thread,istruzione,microistruzione …

### Oggetto

Tipo di dato astratto, procedura, formalità,risorsa logica

All’interno del sistema possiamo avere un Ordinamento parziali per gestire i livelli di sicurezza

### Ordinamento Parziale

L’ordinamento è **PARZIALE,** poiché non tutti i confronti sono definiti (rappresentamento a grafo)

X (tipo gian)

## Primo esempio politica MAC / information flow - I

Prima politica analizzata di tipo Mandatory Access Control

- Soggetto = Utente o programma utilizzato da utente
- Oggetto = Risorsa = File
- Operazioni = read/write/append
- Un utente (sogg./prog) può (Ha il diritto di)
    - Leggere tutti i file che hanno classe minore o uguale alla sua
    - Modificare i record dei file che hanno classe uguale alla sua
    - appendere un record ad un file che ha classe maggiore della sua
    - è necessario anche il permesso di owner che può solo restringere ulteriormente non ampliare all’interno del dominio definito dalle regole owner (need to know)

    No Write Down, privilegia la confidenzialità, tipica del mondo militare


### Downside della “Velia Padula”

## Esempio politica MAC / information flow - II

Seconda politica analizzata di tipo Mandatory Access Control

- Soggetto = Utente o programma utilizzato da utente
- Oggetto = Risorsa = File
- Operazioni = read/write/append
- Un utente (sogg./prog) può (Ha il diritto di)
    - Scrivere tutti i file di una classe minore o uguale alla sua
    - Leggere tutti i file di una classe maggiore o uguale

        —> *Un utente poco affidabile non modificherà dati critici*


    **No Write Up,** privilegia l’integrità, tipica del controllo industriale, si vuole essere sicuri dei valori usati da un impianto nucleare anche a costo di rivelarli a terzi.


## Chinese Wall

- Gli oggetti del sistema sono partizionati in sottoinsiemi
- L’utente che ha operato su un oggetto di un insieme non può operare su quelli in un altro insieme (nozione dinamica, tempo è ininfluente)
- Permette di gestire conflitti di interesse
- È **dipendente dal tempo** = politica dinamica
- È compatibile con MAC perché aggiunge vincoli

## Watermark

- La politica adotta la nozione di livello ma il livello di un soggetto non è fissato ma varia in un certo range e dipende da quello degli oggetti su cui ha operato fino all’istante considerato
- Ad esempio il livello di confidenzialità aumenta dopo che utente legge oggetti di livello elevato
- Ovviamente non diminuisce se dopo legge oggetti di livello minore
- Altra politica che dipende dal tempo come confermato da esempio successivo

## Politica Complessiva

- Una politica reale può combinare politiche diverse. Ad esempio può fondere
    - No write down
    - Chinese wall
- Con questa politica, una volta deciso mediante il confronto tra livelli che un certo soggetto può leggere/scrivere un oggetto, si genera immediatamente un vincolo che impedisce al soggetto di leggere/scrivere alcuni oggetti

# !!! MATRICE DI CONTROLLO DEGLI ACCESSI !!!

La matrice è una struttura dati **estremamente dinamica** che permette di gestire i diritti di un accesso e di un soggetto

XXXCercasi rappresentazione

ACM[i,j] = operazioni che i-esimo soggetto può invocare su j-esimo oggetto.

Una rappresentazione concreta della struttura è condizione

1. **NECESSARIA**
2. **NON SUFFICIENTE**

per il rispetto della politica

## Trusted computing Base

- La politica di sicurezza deve essere comunque realizzata da componenti informatici = esiste una parte di un SI che deve garantire il rispetto della politica di sicurezza del SI
- TCB comprende i componenti del SI che devono implementare (realizzare) la politica di sicurezza
- Se uno di questi componenti è affetto da un **errore** suo o dei componenti che utilizza, allora l’implementazione della **politica non è corretta** e (quasi) sicuramente un qualche soggetto può violare la politica di sicurezza ed invocare operazioni su cui non ha diritto
- Diverso da errore funzionale
- Quindi dobbiamo poterci “fidare “ di questi componenti = garantirne l’affidabilità = assurance

### Le dimensioni della TCB

- Minore è il numero di componenti nel TCB, migliore è la situazione dal punto di vista della sicurezza informatica del sistema informatico considerato
- Dimensione ridotta permette anche di utilizzare di dimostrare formalmente (con metodi matematici) la correttezza del TCB
- La dimensione del TCB è un criterio che permette di confrontare strategie alternative di realizzare una stessa politica di sicurezza = le specifiche del TCB

## VULNERABILITA’

*Def:* Una difetto (bug, errore,…)

- hardware
- software
- nelle persone
- nelle regole della politica

che permette di violare la politica di sicurezza =un soggetto riesce ad eseguire una operazione per cui non ha i diritti.

- Le vulnerabilità esistono con una altissima probabilità in sistemi reali
- Tutte le vulnerabilità sono difetti, non tutti i difetti sono vulnerabilità
- Vulnerabilità più frequente = assunzione non controllata del programma su valori in ingresso o sul comportamento utenti

> La sicurezza informatica NON HA l’obiettivo di risolvere le vulnerabilità: devono invece creare sistemi che permettano il funzionamento degli stessi anche se ci sono parti “affected” da vulnerabilità
>

## Intrusione in un sistema informatico (SI)

- In una intrusione informatica una minaccia esegue una sequenza di azioni/attacchi per raggiungere obiettivo = controllo di oggetti del SI
- Nell’intrusione la minaccia sfrutta una o più vulnerabilità del SI
- Intrusione automatizzata = le azioni dell’intrusione possono essere codificate in o guidate da un programma
- Il programma è definite a partire da exploit = codice per una vulnerabilità
- Quando l’attccante raggiunge obiettivo subentra al proprietario (owner) del sistema e allora può
    - raccogliere informazioni                                                     C
    - modificare informazioni                                                      I
    - impedire ad altri di accedere alle Informazioni                  A


## Fasi di un’intrusione = cosa fa un hacker 😄

1. Attaccante raccoglie informazioni iniziali sul sistema
2. Individuazione (scoperta) delle **vulnerabilità** del sistema per accesso iniziale

    *REPEAT*

    1. Raccolta informazioni su sistema
    2. scoperta vulnerabilità nei component del sistema
    3. costruzione exploit
    4. Azione/Attacco < - > Esecuzione dell’exploit + eventuali azione umante (attaccante può ripeterlo se non ha successo)

        *UNTIL RAGGIUNTO OBBIETTIVO*

3. Installazione di strumenti per il controllo (persistenza)
4. Cancellazione delle tracce dell’attacco
5. Accesso, modifica, …, ad un *sottoinsieme* delle informazioni del sistema o altri attacchi
    1. Information stealing = furto
    2. Cifra e chiedi riscatto

Analizziamo più in fondo

**Intrusione = sequenza di azioni/attacchi**

*REPEAT*

1. Raccolta informazioni su sistema
2. scoperta vulnerabilità nei component del sistema
3. costruzione exploit
4. Azione/Attacco < - > Esecuzione dell’exploit + eventuali azione umante (attaccante può ripeterlo se non ha successo)

    *UNTIL RAGGIUNTO OBBIETTIVO*


Questa fa

- Questa fase può essere vista come una **escalation** di privilegi

## Approcci alla sicurezza

È evidente che intrusioni sono possibili per vulnerabilità questo ci porta a definire due approcci alla sicurezza

### Sicurezza incodizionale

1. Si assume che qualsiasi sia la vulnerabilità nel sistema esista qualcuno interessato ad usarla ed in grado di farlo
2. Quindi tutte le vulnerabilità vanno eliminate

### Sicurezza condizionale =analisi e gestione del rischio

1. Richiede analisi delle minacce (chi è interessato ad attaccare il mio sistema sa come attaccarlo)
- * da finire *

## Analisi del rischio

- Alternativo alla sicurezza incondizionale perhcé esso spesso provoca aumenti non accettabili del costo di un sistema informatico
- approccio guidato dall’economia
    - Cosa possiamo difendere
    - Cosa conviene difendere (sottoinsieme del precedente)

Non esistono ancora metodologie assodate, esiste una foresta di metodi da semplificare e tra cui scegliere
