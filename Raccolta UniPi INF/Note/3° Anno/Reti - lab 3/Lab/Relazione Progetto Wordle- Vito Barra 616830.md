<center>
	<h1>
	Relazione Progetto Wordle 
	</h1>
	<h2>
	 Vito Barra 616830
	 </h2>
</center>

---

## Introduzione
Durante lo sviluppo di questo progetto, in aggiunta alla traccia richiesta ho sviluppato un piccolo framework chiamato _SwitchableDataSource_ utile per la gestione di varie sorgenti di dati e per la memorizzazione di questi. Il framework non è necessario in tutta la sua generalità ma l ho utilizzato per organizzare della lettura e della scrittura dei vari file Json, ogni tanto faro riferimento a questo framework motivo per cui lascio questa nota iniziale. Il codice dal framework sarà nei file consegnati  
<center>
	<h1>
	Client
	</h1>
</center>

## Classi utilizzate
---

### Organizzazione generale
-  _ClientManager_: una classe utile per la gestione delle impostazioni 
	- è __realizzato__ utilizzando il [[Design pattern - Singleton|patter Singleton]] per facilitare l accesso a tutto il codice. per la lettura da Json utilizza il Framework _SwitchableDataSource_ e Gson 
	- è __responsabile__ per la lettura e scrittura delle impostazioni del client e della distribuzione dove serve di questo

### Gestione sessione
- _Client_: una classe per la gestione della sessione di collegamento al server.
	- è __realizzato__ utilizzando il  [[Design pattern - State|patter State]] con quindi un contesto che mantiene lo stato corrente e gli oggetti utili alle funzionalità.  
	- è __responsabile__ della gestione corretto ordine dei messaggi inviati e letti dal server. e del invio di questi ad un oggetto di tipo _UIConsole_
		- GuestClinet:  gestisce lo stato del client che ancora non ha effettuato il login
		- LoggedClient: gestisce il client dopo il corretto login in un account

- _WordleInteractionClient_ : una classe per l invio e ricezione di messaggi dal server
	- è __realizzato__  come collezione di funzioni che interpretano e inviano messaggi da e al server utilizzando la libreria GSON
	- è __responsabile__ del invio e della ricezione di messaggi al server

### Funzionalità client
- _UIConsole_: una classe per la gestione del UI
	- è __realizzato__ come collezione di funzioni  
	- è __responsabile__ stampare l output di reazione ai messaggi messaggi

- _SharedStatReciver_ : una classe per la gestione delle statistiche delle partite condivise degli altri utenti.
	- è __realizzato__ utilizzando il con una semplice lista per salvare i dati in arrivo, la ricezione è tenuta attiva in background grazie al utilizzo di un thread dedicato a questa funzionalità   
	- è __responsabile__ ricezione delle statistiche e del accesso a queste
	

## Struttura Threads del Client
---

### Thread Main
questo thread si occupa della creazione del _ClientManager_  e del client _Client_  e farà partire la gestione della sessione su quest' ultimo oggetto.  il thread si chiude se c è un errore o se si effettua la chiusura della sessione

### Thread SharedStatReciver
Questo thread  si occupa della ricezione in backgroud delle statistiche condivise da gli altri utenti, Viene avviato nel momento di un corretto login con la creazione di un oggetto di tipo _SharedStatReceiver_  e resta attivo fino alla richiesta di logOut da parte del utente e della chiusura del programma. questo thread è un demone 

## Sincronizzazione 
la sincronizzazione tra thread Main e __SharedStatReciver__ è necessaria solo nel momento della lettura dei dati ricevuti. viene effettuata internamente al oggetto __SharedstatReciver__ utilizzando una lista ThreadSafe per memorizzare i dati   

<center>
	<h1>
	Server
	</h1>
</center>

## Classi utilizzate
---

### Organizzazione generale
-  _ServerManager_: una classe utile con le impostazioni globali e per l accesso ai dati persistenti . 
	- è __realizzato__ utilizzando il [[Design pattern - Singleton|patter Singleton]] per facilitare l accesso a tutto il codice. 
	- è __responsabile__ mantenere i vari manager per la gestione dei dati e gestirne gli accessi esponendo funzioni

- _Manager_ : questo vale in generale per tutte le classi nel package Manager. gestiscono La memorizzazione di dati e le operazioni su questi
	- è __realizzato__ come collezione di funzioni e la memorizzazione con delega ad un oggetto IMemoryStrategy dal framework _SwitchableDataSource_
	- è __responsabile__ di esporre le funzionalità sui i dati persistenti  
	
- _ServerWordle_: una classe gestisce il welcome degli utenti     
	- è __realizzato__ con un un ThreadPool che mantiene tutte le connessioni attive che crea ad ogni richiesta di connessione
	- è __responsabile__ della gestione della connessione degli utenti e del avvio della sessione

### Gestione della sessione
- _Session_: una classe per la gestione della sessione di collegamento al server.
	- è __realizzato__ utilizzando il  [[Design pattern - State|patter State]] con quindi un contesto che mantiene lo stato corrente e gli oggetti utili alle funzionalità.  
	- è __responsabile__ della gestione corretto ordine dei messaggi inviati e letti dal client collegato a quella sessione.
		- GuestServer:  gestisce la sessione che ancora non ha effettuato il login
		- LoggedServer: gestisce la sessione dopo il corretto login in un account

- _LoggedUser_: una classe per la gestione delle attività del utente
	- è __realizzato__ come collezioni di funzioni a cui può accedere un utente loggato per modificare lo stato del serve
	- è __responsabile__ di esporre le richieste che l utente loggato può fare al server.
	 
- _WordleInteractionServer_ : una classe per l invio e ricezione di messaggi dal server
	- è __realizzato__  come collezione di funzioni che interpretano e inviano messaggi da e al server utilizzando la libreria GSON
	- è __responsabile__ del invio e della ricezione di messaggi al client 
	
### Funzionalità del server
- _SharedStatSender_ : una classe per la gestione delle statistiche delle partite condivise degli altri utenti.
	- è __realizzato__ incapsulando le funzionalità di creazione invio su gruppo multicast
	- è __responsabile__ invio delle statistiche a tutti gli utenti

- _WordleGameChanger_ : una classe per la gestione delle statistiche delle partite condivise degli altri utenti.
	- è __realizzato__ incapsulando le funzionalità di cambio parola segreta con una ScheduledThreadPool
	- è __responsabile__ gestire il cambio della parola segreta


## Struttura Threads del Server
---

### Thread Main
Questo thread si occupa della inizializzazione delle varie classi Singleton utilizzate nel server. successivamente si mette in ascolto per le connessioni del utente sul oggetto _ServerWordle_  

### N Thread Manager
Ogni Manager ha un Thread per gestire l auto salvataggio dei dati questo thread è gestito direttamente dal oggetto _IMemoryStrategy_ decorato dal un oggetto _AutoSaver_  

### Thread di sessione
Ad ogni sessione viene assegnato un thread dedicato, questi tramite l oggetto _LoggedUser_ accedono e modificano lo stato degli oggetti condivisi del server 

## Sincronizzazione 
La sincronizzazione  tra tutti i thread di sessione sono gestite tramite strutture dati concorrenti come _CopyOnWriteArrayList_ e _CuncurrentHashMap_ queste sono incapsulate nei vari Manager del server e l utilizzo specifico dipende dal manager specifico
La sincronizzazione thread del auto salvataggio nei manager è gestito internamente da  _IMemoryStrategy_   con metodi _Syncronized_.



<center>
	<h1>
	Tipi di dato condivisi
	</h1>
</center>

Le classi condivise tra il programma client e il programma server queste servono principalmente per lo scambio di messaggi tra Client e server
- _Request_ :  da Client a server
- _Response_ : da Server a client 
- _Data_ : oggetti Elaborati dal server e inviati al client 
- _Protocol_ : Regole di interazione tra client e server.

<center>
	<h1>
	Istruzioni per l'utilizzo
	</h1>
</center>

Per il corretto utilizzo del programma necessita di un console che supporta i caratteri ANSI. ho quindi allegato insieme ai Jar una cartella con una console portatile che supporta questi caratteri. Questa è una soluzione per WINDOWS

Si può avviare il Jar anche con il semplice doppio click ma il risultato sarà presso che inutilizzabile

## Informazioni generali
- Il programma è compilato con Java 17 LTS
- L unica libreria usata è GSON
	- la libreria non è presente come allegato perché presente direttamente nei file jar

## Corretto Avvio del Programma
1. Inserire nella cartella del server il file del vocabolario delle parole da utilizzare  
2. Aprire la cartella ANSICON presente nella cartella della consegna
3. Scegliere la versione corretta tra x86 e x64 a seconda del sistema operativo
4. Avviare il programma "_ansicon.exe_" questo avviare la console con il supporto ANSI
5. Navigare nella console fino alla cartella del server 
	1. Avviare il server con il comando _Java -jar_  "ServerWordle.jar"
6. Aprire altre istanze di ANSICON 
7. Navigare nella console fino alla cartella del client 
	1. Avviare il server con il comando _Java -jar_  "ClientWordle.jar" 

## Utilizzo
1. Il __server__ tramite la console offre alcune funzionalità extra
	- Vedere le parole che vengono estratte
	- Forzare il cambio di parola con l apposto comando
	- Chiusura del server 
  La sintassi e la semantica dei comandi viene scritta in console al avvio del programma 
2. Il __client__ tramite la console 
	- permette l interazione con il server
   Tutti i comandi disponibili vengono presentati sulla console


