R2022-09-21 RETI TEORIA
Reti di calcolatori: modello architettura le e stack di protocolli alla base di internet 

Protocolli
- Routing 


Cos é internet? Interoperabilità di multiple reti diverse sia in tipo che in dimensione 

### protocolli :
- regole di comunicazione definito dallo standard IETF
### Componenti di una rete su internet:
- end Device (o sistemi terminali ) (Host):
	- Dispositivi  (pc, smartphone, ecc)
	- Server (di solito in data center)
- Link :
	- Infrastrutture di collegamento
- Dispositivi di interconnessione:
	- Router : connette Una rete a internet 
	- Nore: l internet provider è fatto da solo router e fa da snodo alla connessione 
- Switch: collega gli host al router 
### servizi
- I servizi è ciò che la rete offre al livello applicativi  


# tipi di reti Divisi per grandezza:
- LAN: Local Area network
	- Topologia di comunicazione :
		- BUS (non più usato per problemi di collisione)
		- A Stella  (punto di comunicazione centralizzato, più comune oggi ) 
- WAN: Wide Area Network:
	seve a connettere tra di loro più LAN
	- Topologia di comunicazione:
		- Punto Punto:
		- Commutazione: in comunemente usata da  un internet service provide 
	- Esempi:
		- Rete di Ricerga GARR


# ISP
Per collegare I vari Host c è bisogno di ISP (internet servic pprovider) che danno i percorsi per connettere i diversi host. Per connettere gli ISP  si utilizza degl Internet exchange point che servono per mettere in comunicazione host che si connetto ad ISP diversi. Possono esserci anche delle connessione dirette. c è una gerarchia degli ISP 

(aggiungere foto )




tim Bernal clive Ted X  (vedere per lo standard HTTP)

# livelli di stack 
- Application
- Network 
- Link 


# Modello dati top-Down vs bottom-up
modello a clessidra inserire immagine 


Negli anni la richiesta di stress sulla rete è in aumento (inserire immagine Grafico )


2022-09-23: RETI  

## Commutazione di pacchetti e commutazione di circuito 

Una internet e una interconnessione di reti composte da link e dispositivo capaci di. Scambiarsi informazioni.
- sistemi terminali (host)
- Dispositivi di intercomunicazione che si trovano sul percorso

### problema:
  bisogna trovare un percorso da l host sorgente al hos t destinatario. Per fare questo abbiamo le _tecniche di commutazione_: 
  - ## circuit-switch: 
	  - dedicare le risorse alla comunicazione che si vuole fare 
	  - dura per tutta la durata della comunicazione
		  - pro: 
			  - la performance è garantita siccome la connesione resta stabile 
			  - Tariffazione facile
		  - contro:
			  - Fase di SetUp: gestire la richiesta di comunicazione che arriva alla rete, calcolare le risorse necessarie e assegnare quelle risorse  
			  - Spreco di risorse: queste restano in attive se non utilizzate 
				  - (es.  nelle telefonate durante i silenzi non si sta usando la risorsa assegnata )
	  - tecnica di riserva delle risorse: 
		  - _Frequency Division Multiplexing_ (FDM):  la bambina totale di frequenza viene divisa in sotto bande più piccole e ogni comunicazione diversa ha una manda fissa per tutta la durata della comunicazione 
		  - _Time Division Multiplexing_(TDM): divido l intervallo in tempi più piccoli e per ogni intervallo di tempo un utente puo utilizzare tutte le frequenze 
  - ## commutazione di pacchetto: 
	  - il messaggio viene diviso in unita Della comunicazione chiamati pacchetti.
	  - i pacchetti vengono inviati sulla rete che li instrada vero l host destinazione.
	  - La rete è in condivisione di risorse ovvero più pacchetti di comunicazioni anche diverse possono usare la stessa risorsa per arrivare a destinazione 
	  - pacchetti della stessa comunicazione possono seguire strade diverse per arrivare a destinazione. 
		  - Questo perchè la strada iniziale potrebbe vararla siccome potrebbe congestionare o i potrebbe aprire una  percorso migliore.
		  - I router utilizzano le tabelle di inoltro per instradare i pacchetti che si aggiornano meno spesso del tempo di trasmissione di un messaggio 
	  - _stora e forward_ : 
		  - Il router deve ricevere l intero pacchetto prima di poterlo inviare
			  - Facendo cosi c è un ritardo di accostamento siccome devono arrivare pi pachetti
			  - Se i pacchetti sono troppi non entrano nel buffer e quindi c è una perdita dei pacchetti
	  - i pacchetti sono grandi mediamente 500 byte
  - Pro:
	  - Risorse trasmissive usate solo se necessario
	  - Segnalazione non richiesta
  - Svantaggi:
	  - Tecnologie di inoltro non efficienti (necessita di selezionare l uscita per ogni pachetto
	  - tempo di elaborazione ai router (rooting table lookup )
	  - Accostamento al router
	  - Protocolli necessari per un trasferimento dati affidabile controllo della congestione 
  -  La commutazione di pacchetti gioca sul fatto spesso non tutti gli utenti sono attivi sul mezzo di comunicazione quindi ad esempio se una reta dovesse essere in grado di supportare 10 utenti attivo potrebbe supportare 35 utenti in totale che attività ”alternate”


Parametri delle reti:
- larghezza di Banda (bandwitdth):
- Velocità di trasmissione:
- Throughput: quantità di dati che possono essere trasmessi con successo da un nodo siorgente ad un nomo destinazione in un cero intervallo di tempo 
- Throughput < velocità di trasmissione 
	- Casi di collo di bottiglia 
- Il Throughput Non ha una definisiozne precisa dipende da cosa dobbiamo misurare
	- Caso di mezzo trasmissivo : il rate massimo oltre il quale si hanno sistematicamente perdite 
- Latenza:
	- Ritardo di accostamento:
		- Dipende dal intensità e dal tipo di traffico
		- _difficile da gestire_
	- RItardo di elaborazione al nodo: 
		- Controllo errori sui bit 
		- Decidere indirizzo di destinazione (ritardo di elaborazione)
		- 
	- Ritardo di trasmissione: 
		- Devo conservare e mandare l intero pacchetto e il ritardo provocato da questo arrivo si calcola con Lunghezza del pachetto / velocità di tarasmissione 




Standard: IO-OS


2022-09-30:
## ISO/OSI VS TCP/IP
ISO/OSI
- Generale
- Definizione di servizio interfaccia e protocollo
- - poco efficiente alcuni livelli poco utili
- Standard difficile
- Telco-oriented
- Poca tempestivo
- 

TCP/IP
- Standard de facto
- Implementation driven 
- Specifiche non astratte e rigoroso
- Modello non generale

Esistono altri protocolli per risolvere problemi ad hoc difficile da rimpiazzare 


## Livello Applicativo
- le applicazioni formate da processi distribuiti si più terminali (end host)

Il livello applicativo parla con un altro livello applicativo , per farlo manda un messaggio in una connesione logica tra i due livelli applicativi, questo si tradurrà nello scendere lo stack TCP e passare varie tecnologia 

Il protocollo definisce i i tipi di messaggi scambiati a livello applicativo 
La sintassi de vari tipi di messaggio 



### paradigmi:
- Client-Server:
- Peer-to-Peer: peer che possono offrire servizi e iniziare richeste.
- 


Io: 32bit per indirizzare un processo nello specifico serve una socket e la socket si utilizza l ip e una porta 

## TDP UDP


Da vedere dalle slide


# Word Wide Web
- un è normale collezion di informazioni nella quale le risorse sono distribuite e collegate l una all altra
- Qualsiasi server web nel mondo puo aggiungere risorse
- Basato su HTTP


## Uniform resource Identifier (URI)


## Uniform resource Locator (URL)
sotto insieme di URI che identifica le risorse attraverso il loro meccanismo di accesso

### sintassi 
	<schema>://<user>:<password>@<host>:<port>/<path>
- _user_ e _password_ opzionali e generalmente deprecato
- Scheme: protocollo di accesso alla risorsa
- host= nome di dominio di un ghost o indirizzo IP
- Port= homer si porta del servere di solito si unasono quelle di default
- Path= contiene dati per l host e schema e identifica la risorsa nel contesto di quello schema e host puo consistere in una sequenza di segmenti sperata di / ad esempio nel file system del serv3e ma non solo il pat specifia la REquest-URI

## Uniform resource Naming (URN)
Sottoinsieme di URI che deve o rimanere globalmente unici e persistente anche quando la risorsa cessa di esistere e diventa non disponibile 

  _query_
	string di informazione che deve essere interpretata
	 dal servere 
URL assoluta:
URL Relativa:






2022-10-06: LAB

Utilizzare collezioni Thread Safe per la sincronizzazione con i thread. La composizione di operazioni potrebbero non funzionare a dovere in realtà queste collezioni sono Conditionale Thread Safe. 





2022-10-13:


## accesso alla rete
- TCP: è connection full e puo essere paragonato a una chiamata telefonica dove viene stabilito  prima un canale virtuale : visto come uno string
	- SochetStream
		- ClientSoket: 
		- ServerSoket: 
UDP: è connection less non c è un canale determinato e quindi ogni pachetto passa in percorsi diversi : visto come pachetto
	- DatagramSochet

Nome DI dominio: 
	DNS: Domina name sistem  Traduce i nomi in indirizzi IP 

_InetAddress_: classe per la gestione di indirizzo ip sia ipv4 che ipv6
Il primo campo è un IP il secondo il nome del dominio.
Non ha costruttore publici le instanze sono generate da metodi statici della stessa classe che larendono una  [[classe factory]] di se stessa.

I metodi di InetAddress sono cheshati siccome è molto lento interrogare l internet 
	I tempi della permanenza i chace sono spettabili dalle impostazioni della JVM
	Si fa dalla classe 
	Java.Security.Security.setProperty(”network address.cache.ttl”,CACHINGTIME );


Con _InetAddress_ ci sono metodi che contattano il DNS altre che Non lo fanno per crare una connessione locale magari in rete locale dove conosc sia il nome che direttamente l indirizzo IP.
Ci sono anche metodi di istanza.


## Paradigma Clinet-Server 

è una comunicazione Asimmetrica ovvero il client richiede il servizio al server e il server risponde. 

In java le API di connessione sono state pensate apposta sul questo paradigma 

Su ogni serve un servizio viene indicato da una porta ogni porta si riferisce ad un servizio questa è un astrazione di cosa c è effettivamente al implementazione del servizio 


Per la connessione si utilizzano i socket differenzianti in
- socketClient
- SocketServer



## DNS : Domain Name System
Serve a tradurre dei  "nomi" in undirizzi Ip per accedere a delle macchine
ha piu vantaggi
1. disaccopiare l ip fisico e il nome del servizio 
	1. grande vantaggio siccome puo succeder che per lo stesso nome possono essere associati piu ip o possono cambniare nel tempo
2. nomi piu human Frendly
Il DNS è un servizio di [[livello applicativo]]



è realizato come 
1. uno schema di assegnazione dei nomi gferarchico e basato su domini
2. un database distribuito conteneente i nomi e le corrispondenze con gli indirizzi ip iomplementato con una gerarchia di name server
3. un protocollo per la distribuzione della informazini sui nimi tra name serrver
	- host router name server comunicano per risolvere nomi traduzione nome indirizzo
	- utilizzando UDP (avvolte TPC nel trasferimento di DB)


per gestire piu nomi dello stesso Ip si utilizzano Alias 

puoi fare bilanciamento di carico sulla rete, se un nome ha piu Ip conessi ad ogni domanda ne da uno diverso a rotazione cosi ogni macchina ha un carico simile alle altre.


è uganizato gerarchicamente 
	quindi un nome è del tipo
		\[sistema1\].\[sistema2\].\[sistema3\].\[sistema4\]
	per garantire l univocita del nome si ci si basa che ogni livello lo garantisca per tutti i nomi sostostanti 




il processo di traduzione da nome a Ip il client prima chiede al LOCAL DNS se ha la truzione la rstituisce altrimenti reinoltra al Dns di gerarchia superiore fino ad arrivare al root name server che sono DNS di  livello 0 che ha lo scopo di tenere le associazione a tutti gli altiri DNS  di primo livello. ad ognmi livello ovviamentre c è della cache.

il DNS root sono pochi nel mondo meno di 1000.

### Query Ricorsiva
![[Pasted image 20221026034606.png]]
![[Pasted image 20221026034547.png]]

Contro: Molti passaggi 

### Query Iterativa
![[Pasted image 20221026035044.png]]
![[Pasted image 20221026035032.png]]
vantaggio: Il root nome server viene utilizzato una sola volta cosa migliore visto che sono pochi.

viene conservata un associazione in cache e nel informazione c è anche un Timeoud che da il tempo di persistenza del record di quella cache.  
![[Pasted image 20221026035524.png]]