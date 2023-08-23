---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocollo Secure socket layer (SSL)
---
il  _protocollo Secure socket layer_  serve per gestire connessioni sicure tra _utenti_, molti utilizzato per gestire le situazioni in cui un utente vuole accedere ad un servizio e per fare ciò deve mandare dei dati sensibili ad es numero carte di credito.

ponendo che un utente $U$ voglia accedere ad un servizio in un sistema $S$ con il protocollo SSL la comunicazione è _riservata_ siccome si utilizza un [[Cifrari ibridi|cifrario ibrido]] ed è garantita l _autenticazione_ accertando del identità dei due utenti usando [[Certification Authority|certificati]] e apponendo un MAC ad ogni messaggio.

Questo protocollo viva tra il [[Livello Applicativo|livello applicativo]] e il [[Livello di trasporto|livello rete]] 

#### Organizzazione generale
l organizzazione del _protocollo SSL_ è su due livelli 
_SSL record_: 
	più in basso nello stack è connesso al [[Livello di trasporto|livello trasporto]],  ha il compito di incapsulare i messaggi dai livelli superiori per garantire _confidenzialità_ e _interita_ del messaggio
_SSL HandShake_: 
	più in alto nello stack fa da interfaccio al [[Livello applicativo|Livello applicativo]]e permette agli utenti di negoziare gli algoritmi di cifratura e [[Protocolli di firma digitale|firma digitale]] e stabilire le chiavi per gli algiritimi usati e per il MAC 
abbiamo quindi che _SSL HandShake_ crea un canale sicuro tra due utenti attraverso la selezione di un _suit crittografica_ e poi sarà _SSL record_ a criptare e inviare quel messaggi.


#### SSL HandShake
ponendo che l utente $U$ detto _client_ voglia accedere ai i servizi di sistema $S$ detto _server_, abbiamo che in questo protocollo i due cooperano per creare delle _chiavi segrete_ da utilizzare per le comunicazioni successive. 
Client e serve si accordano su un solo segreto il _master secret_ che costruiscono insieme in modo incrementale.
seguendo il seguente schema:
![[Pasted image 20230817012508.png]]

1. _Utente: client hello_:
	  L’utente $U$ manda al sistema $S$ un messaggio, detto _client hello_, con cui richiede la creazione di una connessione SSL, specifica le “prestazioni” di sicurezza che desidera siano garantite durante la connessione, e invia una sequenza di _byte casuali_.  il messaggio specifica:
	  - la _versione del protocollo_ SSL eseguito da $U$
	  - un _elenco di [[Algoritmi di compressione|algoritmi di compressione]]_
	  - una _lista di cipher suite_, cioè di cifrari e meccanismi di autenticazione che $U$ può supportare _ordinati secondo le sue preferenze_. 
2. _Sistema: server hello_:
	  Il sistema $S$ riceve il messaggio di _client hello_ e seleziona da questo un _cipher suite_ e un _algoritmo di compressione_ che anch’esso è in grado di supportare. Dopodiché invia all’utente un messaggio, detto _server hello_, che specifica la sua scelta e contiene una _nuova sequenza di byte casuali_
	  Se $U$ non riceve il messaggio di _server hello_, interrompe la comunicazione.
3. _Sistema: invio del certificato_:
	  Solitamente il sistema si autentica con l’utente inviandogli il proprio _[[Certification Authority|certificato digitale]]_. Siccome esistono più _Certification Authority_ (_CA_)  organizzate in una struttura ad albero, nel caso in cui  $U$ e $S$ si “affidino” a _CA_  differenti il sistema invia all’utente una sequenza di certificati ordinati in accordo alla _CA_ che li ha firmati, da quella che ha certificato $S$ a quella che è alla radice dell’albero delle _CA_.
	  Nel caso in cui i servizi offerti da $S$ debbano essere protetti negli accessi, il sistema _può richiedere all’utente_ di autenticarsi inviando il suo [[Certification Authority|certificato digitale]] 
4.  _Sistema: server hello done_:
	   Il sistema invia il messaggio _server hello done_ con il quale sancisce la fine degli accordi sul _cipher suite_ e sui parametri crittografici ad essa associati. 
5.  _Utente: autenticazione del sistema_.
	   Per accertare l’autenticità del certificato ricevuto dal sistema, $U$ controlla che la data corrente sia inclusa nel periodo di validità del certificato, che la CA che ha firmato il certificato sia tra quelle fidate e che la firma da essa apposta sia autentica. Nel caso che $S$ invii una lista di certificati, $U$ esegue la relativa catena di verifiche. 
6. _Utente: invio del pre-master secret e costruzione del master secret_:
	  L’utente $U$ costruisce un _pre-master secret_ costituito da una nuova sequenza di _byte casuali_, lo cifra con il cifrario a chiave pubblica del _cipher suite_ su cui si è accordato con $S$ e spedisce il relativo crittogramma a $S$. Il _pre-master secret_ viene inoltre combinato da $U$ con alcune _stringhe note_ e con i byte casuali presenti sia nel messaggio di _client hello_ che in quello di _server hello_. A tutte queste sequenze l’utente applica le funzioni [[Funzioni Hash One-Way|hash one-way]] SHA1 e MD5 secondo una combinazione opportuna. Il risultato costituisce il _master secret_
7. _Sistema: ricezione del pre-master secret e costruzione del master secret_.
	  Il sistema decifra il crittogramma contenente il _pre-master secret_ ricevuto dall’utente e calcola il _master secret_ mediante le stesse operazioni eseguite dall’utente nel passo 6, in quanto dispone delle stesse informazioni. 
8.  _Utente: invio del certificato (opzionale)_:
	  Se all’utente viene richiesto un certificato (passo 3) ed egli non lo possiede, _il sistema interrompe l’esecuzione del protocollo_. Altrimenti l’utente invia il proprio certificato con allegate una serie di informazioni firmate con la sua _chiave privata_, che contengono tra l’altro il _master secret_ che egli stesso ha generato e tutti i messaggi scambiati fino a questo momento (_SSL-history_). $S$ controlla il certificato di $U$ con operazioni simmetriche a quelle eseguite da $U$ nel passo 5, e verifica l’autenticità e la correttezza della _SSL-history_. In presenza di anomalie la comunicazione con $U$ viene interrotta.
9.  _Utente/Sistema: messaggio finished_
	  Questo messaggio è il primo ad essere protetto mediante il _master secret_ e il _cipher suite_ su cui i due partner si sono accordati. Il messaggio viene prima costruito dall’utente e spedito al sistema, poi costruito dal sistema e spedito all’utente: nei due invii la struttura del messaggio è la stessa ma cambiano le informazioni in esso contenute. La sua costruzione consta di due passi. All’inizio si concatenano il _master secret_, tutti i messaggi di handshake scambiati fino a quel momento e l’identità del mittente ($U$ oppure $S$). La stringa cosi ottenuta viene trasformata applicando le funzioni SHA1 e MD5, dando origine a una coppia di valori che costituisce il messaggio finished. Questo messaggio è diverso nelle due comunicazioni poichè S aggiunge ai messaggi di handshake anche il _messaggio finished_ ricevuto dall’utente. Il destinatario della coppia ($U$ oppure $S$) non può invertire la computazione precedente in quanto generata da funzioni one-way, ma ricostruisce l’ingresso delle due funzioni SHA1 e MD5, ricalcola queste funzioni e controlla che la coppia cosi generata coincida con quella ricevuta, come dimostrazione che la comunicazione è avvenuta correttamente.



 > [!example]- esempio di suit di cifrari
 > la cipher suite indicata con la sigla _SSL_RSA_WITH_2TDEA EDE_CBC_SHA1_ prevede RSA per lo scambio delle chiavi di sessione; 2TDEA EDE CBC per la cifratura simmetrica, ove EDE indica la sequenza encryption-decryption-encryption per il Des Triplo con due chiavi 2TDEA e CBC indica l’impiego di un [[Cifrario a Composizione di blocchi|cifrario a composizione di blocchi]] ( e prevede SHA1 come [[Funzioni Hash One-Way|funzione hash one-way]] per il calcolo dei [[Protocolli di Autenticazione|MAC]].
 
### SSL Record
Il canale sicuro approntato dal protocollo SSL Handshake viene realizzato dal protocollo SSL Record. I dati sono frammentati in blocchi di lunghezza opportuna; ciascun blocco viene numerato, compresso, autenticato attraverso l’aggiunta di un MAC, cifrato mediante il cifrario simmetrico su cui l’utente e il sistema si sono accordati, e finalmente trasmesso dall’SSL Record utilizzando il protocollo di trasporto sottostante. Il destinatario della comunicazione esegue un procedimento inverso sui blocchi ricevuti: decifra e verifica la loro integrità attraverso il MAC, decomprime e rassembra i blocchi in chiaro, infine li consegna all’applicazione sovrastante

#### Sicurezza del protocollo
Il protocollo SSL si potrebbe utilizzare anche senza i certificati e  l utente $U$ e il server $S$ si scambieranno il _pre-master Secret_ tramite l utilizzo di altri protocolli  che utilizzano cifrari assimetrici come il [[Cifrario Diffie-Hellman (DH)|protocollo diffi-helman]], ma questo lo espone il protocollo ad attacchi di tipo [[Tipologia di attacchi ai cifrari|man in the midle]]

Se invece si usano i certificato allora la comunicazioni e _confidenziale_ e _affidabile_ e questo avviene da come sono state progettati le fasi:


_Client hello e server hello_:
	Nei passi di _hello_ i due partner creano e si inviano due _sequenze casuali_ per la costruzione del master secret, che risulta cosi diverso in ogni _sessione di SSL_. Questo impedisce a un crittoanalista di riutilizzare i messaggi di handshake catturati sul canale in una sessione precedente, per sostituirsi a $S$ in una successiva comunicazione con $U$ (attacco di reply).
_MAC dei blocchi di dati_:
	Il protocollo _SSL Record_ numera in modo incrementale ogni blocco di dati e autentica il blocco attraverso un _[[Protocolli di Autenticazione|MAC]]_. Per prevenire la modifica del blocco da parte di un crittoanalista attivo, il MAC viene calcolato come immagine [[Funzioni Hash One-Way|hash one-way]] di una stringa costruita concatenando il contenuto del blocco, il numero del blocco nella sequenza, la chiave del MAC, e alcune stringhe note e fissate apriori. La specificazione del numero del blocco consente di prevenire l’impiego fraudolento e iterato del blocco stesso nell’ambito della stessa sessione (_attacco di reply_), perchè si dovrebbe cambiare quel numero e il _MAC_ corrispondente. 
		(Una conseguenza negativa per gli utenti `e per`o che, se un blocco viene perduto nella trasmissione, i blocchi successivi devono essere ricreati e spediti nuovamente). 
	Poich´e i _MAC_ sono cifrati insieme al messaggio, un crittoanalista non può alterarli senza aver forzato prima la chiave simmetrica di cifratura: quindi un attacco volto a modificare la comunicazione tra i due partner è difficile almeno quanto quello volto alla sua decrittazione.
_Il sistema è autenticato_:
	Il canale definito dal protocollo _SSL Handshake_ è immune da attacchi del tipo [[Tipologia di attacchi ai cifrari|man in-the-middle]] poichè il sistema viene autenticato con un _[[Identificazione, autentificazione, Firma digitale|certificato digitale]]_. L’utente ha cosi la possibilità di comunicare il _pre-master secret_ al sistema in modo sicuro attraverso la chiave pubblica presente nel certificato di $S$. Solo $S$ può decifrare quel crittogramma e quindi costruire il corretto _master secret_, su cui si fonda la costruzione di tutte le chiavi segrete adottate nelle comunicazioni successive. Quindi solo il sistema $S$, ossia quello a cui si riferisce il certificato, potrà entrare nella comunicazione con l’utente $U$. 
_L’utente può essere autenticato_: 
	Il certificato dell’utente (se richiesto) e la sua firma apposta sui messaggi scambiati nel protocollo (_SSL-history_) consentono al sistema di verificare che l’utente è effettivamente quello che dichiara di essere e che i messaggi sono stati effettivamente spediti da esso. Se ciò non si verifica, il sistema deduce che il protocollo è stato alterato casualmente o maliziosamente e interrompe la comunicazione.
	il certificato del utente è opinali siccome è difficile per un utente riuscire a procurarsi un certificato. infatti questo è il motivo del successo di questo protocollo e per garantire l [[Protocolli di Identificazione|identificazione]] del utente si preferisce usare metodi tradizionali come un _login_
_Il messaggio finished_:
	questo messaggio viene costruito in funzione del _master secret_ e contiene tutte le informazioni che i due partner si sono scambiati nel corso dell’handshake. Lo scopo è quello di consentire ai due partner di effettuare un ulteriore controllo sulle comunicazioni precedenti per garantire che queste siano avvenute correttamente, che essi dispongano dello stesso _master secret_, e che la loro comunicazione non sia stata oggetto di un attacco attivo.
 _Generazione delle sequenze casuali_:
	Le tre [[Generazione di numeri Pseudo Casuali|sequenze casuali generate]] dall’utente e dal sistema e comunicate nei messaggi di _client hello, server hello_ e _pre-master_ secret entrano in gioco nella creazione del _master secret_ e quindi nella generazione delle chiavi di sessione. In particolare la sequenza corrispondente al _pre-master secret_ viene generata dall’utente e comunicata per via cifrata al sistema. La non predicibilità di questa sequenza è uno dei fulcri su cui si fonda l’intera sicurezza del canale _SSL_: una sua cattiva generazione renderebbe il protocollo molto debole, ribadendo l’importanza che rivestono i [[Generazione di numeri Pseudo Casuali|generatori pseudo-casuali]] nei processi crittografici
