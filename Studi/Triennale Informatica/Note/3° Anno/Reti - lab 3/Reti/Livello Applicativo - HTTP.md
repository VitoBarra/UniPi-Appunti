---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Livello Applicativo - HTTP
---
l _HyperText Transfer Protocol_ (HTTP) è un protocollo di [[Livello Applicativo]] questo è
- del tipo richiesta/risposta :
	- _Client HTTP_ : programma che manda le richieste al server
	- _Server HTTP_: programma che accetta richieste e risponde con messaggi di risposta
	- ![[Pasted image 20230103020019.png]]
- è _Stateless_: è senza memoria di stato e questo rende le coppie richiesta risposta sono indipendenti.
- Usa [[Livello trasporto - TCP|TCP]] (è _connection oriented_)
	- Il client richiede l istaurazione di una connessione TCP con il server
	- i processi si scambiano messaggi attraverso le rispettive [[Interfaccia Socket|Socket]] per la comunicazione


## Connessione
la connessione è un circuito logico di [[Livello di trasporto]] stabilita tra i due programmi applicativi, questo è usato per la comunicazione
può essere:
- _Non persistente_(http1.0: RFC 1945): viene stabilita una connessione [[Livello trasporto - TCP|TCP]] sperata per recuperare ciascuna [[WWW - Word Wide Web#Uniform resource Identifier (URI)|URI]] 
- _Persistente_ (http1.1: RFC 2616):  il client può assumere che il server mantenga la sua connessione attiva e può quindi mandare altre richieste sulla stessa connessione. la chiusura della connessione avviene se il client lo richiede con un messaggio ed è specificato nel _header_ o se c è in _Time out_. Una volta che la connessione chiusa il client non potrà più mandare messaggi su quella connessione


### http1.1
#### Vantaggi di una connessione persistente
- Vengono aperte e chiuse meno connessioni TCP quindi si risparmia CPU-Time 
- Ritardi delle connessioni successive ridotti siccome non si deve aspettare la riapertura della connessione
- Gestione più efficace del controllo di congestione

## Pipelining
è una tecnica per aumentare ulteriormente le prestazioni della connessione
consiste nel mandare più richieste di più oggetti senza aspettare prima la risposta
- _le risposte_ devono arrivare nel ordine di richiesta il che può portare a problemi se si deve soddisfare una richiesta molto pesante come prima (Head of Line Blocking).
	- in questi casi non si raggiunge l obbiettivo di diminuire il tempo di caricamenti
- il client _può_ mandare richieste in pipeline solo se queste sono _idempotenti_
![[Pasted image 20230103022133.png]]

## Messaggi scambiati
i messaggi possono essere di due tipi _richiesta_ e _risposta_ ed è composto da 
- _Start-Line_: la riga iniziale che differenzia richiesta e risposta
- serie di  _header_: ovvero coppie nome-valone che specificano alcuni parametri del messaggi trasmesso o ricevuto
	- _general Header_: relativi alla trasmissione 
		- Es. Data, codifica, connessione, 
	- _Entity Header_:  relativi all’entità trasmessa 
		- Content-type, Content-Length, data di scadenza, ecc. 
	- _Request Header_: relativi alla richiesta 
		- Chi fa la richiesta, a chi viene fatta la richiesta, che tipo di caratteristiche il client è in grado di accettare, autorizzazione, ecc. 
	- _Response Header_: nel messaggio di risposta 
		- Server, autorizzazione richiesta, ecc.
- _body_: il corpo del messaggio che è opzionale

#### Request 
![[Pasted image 20230103023657.png]]
- Request-Line:
	- _Method_: operazione che il client richiede venga effettuata sulla risorsa identificata dalla Request-URI. Definizione della semantica dei metodi nella
	  ( RFC 2616 )
	- _HTTP-Version_: il mittente indica il formato del messaggio e la sua capacità di comprendere ulteriori comunicazioni HTTP
- Heaers: 
	- ![[Pasted image 20230103024953.png]]
#### Response 
![[Pasted image 20230103023724.png]]
- Status-Line:
	- _HTTP-Version_: la versione di HTTP supportata
	- _Status-Code_: intero a tre cifre che rappresenta un codice di risultato dell’operazione richiesta
		- lo standard definisce: ![[Pasted image 20230103025034.png]]
		- Alcuni esempi sono ![[Pasted image 20230103024216.png]]
	- _Reason-Phrase_: descrizione testuale dello Status code (pensata per l’utente umano)
- _Reposne Heaers_: informazioni che non possono essere insertite nella status line
	- ![[Pasted image 20230103025116.png]]

## Content Negotiation
le risorse possono essere disponibili in più rappresentazioni e la contente negotiation si occupa di selezione la rappresentazione più appropriata per la richiesta fatta. la rappresentazione viene scelta sulla base di Request e Entity headers.
![[Pasted image 20230103025154.png]]
esempi di rappresentazioni diverse sono un diverso formato o una diversa lingua.


## Request Method
- _OPTIONS_: richiede solo le opzioni di comunicazione associate ad un URL o al server stesso (le sue capacita , metodi esposti)
	- ![[Pasted image 20230103210312.png]]
- _GET_: metodo richiede il trasferimento di una risposta indentificata da una URL o operazioni associate al URL stessa.
	- Sono possibili _Conditianl get_ aggiungendo le condizioni nel header
		- Header: 
			- if-Modified-Since, If-Unmodified-Since (date);
			- if-Match, if-None-Match (ETag); or If-Range
		- ![[Pasted image 20230103214326.png]]
		- ![[Pasted image 20230103214315.png]]
	- conditional GET
		- Header: Range
		- ![[Pasted image 20230103210642.png]]
- _HEAD_: Simile al GET, ma il server non trasferisce il _message_ body nella risposta. Utile per controllare lo stato dei documenti (validità, modifiche, cache refresh).
	- ![[Pasted image 20230103210736.png]]
	- ![[Pasted image 20230103210756.png]]
- _POST_:
	- il metodo POST serve per inviare dal client al server informazioni inserite nel body del messaggio
	- Si dovrebbe utilizzare per 
		- il metodo POST è usata per chiedere che il server accetti l'entità (risorsa) nel corpo della richiesta come una nuova subordinata della risorsa identificata dalla _Request-URI_ nella _Request-Line_
	- nella realtà dei fatti   
		- La funzione effettiva eseguita dal POST è determinata dal server e dipendente tipicamente dalla Request-URI. Esempi: Annotazioni ad URL esistenti, FORMs, Posting a message boards, newsgroups, mailing list, etc., scrittura su database
	- ![[Pasted image 20230103211347.png]]
- _PUT_: il client chiede al server di creare/modificare una risorsa
	- Il client specifica nella _Request URI_ l’identificativo della risorsa 
	- questa è successivamente recuperabile con un  GET 
	- ![[Pasted image 20230103215223.png]]
- _DELETE_: il client chiede di cancellare una risorsa identificata dalla Request URI


>[!note]
>- _Post_ e _Delete_ sono metodi che solitamente non sono esposti
>- Safe-Method: non modificano lo stato e sono:
>	- GET, HEAD, OPTIONS, TRACE
>- _Idempotent-methods_: metodi che se chiamati $N>0$ volte hanno lo stesso effetto di una sola chiamata sono:
>	- GET, HEAD, PUT, DELETE, OPTIONS, TRACE



## Web Cahing 
- Serve a soddisfare richiesta del cliente senza contattare server 
- Memorizzare copie temporanee di risorse Web (es. pagine HTML, immagini) e servirle al client per ridurre l’uso di risorse (e.g. banda, workload sul server) e diminuire tempo di risposta al client 
- User Agent Cache: Lo user agent (il browser) mantiene una copia delle risorse visitate dall’utente 
- Proxy Cache 
	- Il proxy intercetta il traffico e mette in cache le risposte. Successive richieste alla stessa Request-URI possono essere servite dal proxy senza inoltrare la richiesta al server 
	- Utente configura il browser: accessi Web via proxy

![[Pasted image 20230103211829.png]]
l'utente configura il browser in modo che punti a una cache Web il browser invia tutte le richieste HTTP alla cache 
se l’oggetto è nella [[Cache]]: la cache restituisce l'oggetto al client 
Altrimenti la cache richiede l'oggetto dal server di origine, memorizza nella cache l'oggetto ricevuto, quindi restituisce l'oggetto al client
![[Pasted image 20230103211840.png]]

La cache Web funge sia da client che da server: 
- Server per il client richiedente 
- Client verso il server di origine 
- Web cache può essere fornita installata dall'ISP (università, azienda, ISP residenziale)

#### Vantaggi
 - ridurre i tempi di risposta 
 - la cache è più vicina al client 
 - ridurre il traffico sul collegamento di accesso di un istituto 
 - consente ai «piccoli» fornitori di contenuti di fornire contenuti in modo più efficace


## Cookie
questi sono dei tocken ma mantenere dello stato e servono siccome il protocollo HTTP è stateless. ma ci sono applicazioni che hanno bisogno di stato per funzionare qui entrano in gioco i cookie, questi sono utili per associare ad un utente un certo stato facendosi "riconoscere" presentando il cookie


![[Pasted image 20230103212219.png]]
![[Pasted image 20230103212239.png]]

- Funzionamento: 
	- cliente C invia a server S normale richiesta HTTP 
	- server invia a cliente normale risposta HTTP + linea _Set-cookie:_ 1678453 
	- cliente memorizza cookie in un file (associandolo a S) e lo aggiunge con una linea cookie: 1678453 a _tutte le sue_ successive richieste a quel sito 
	- server confronta cookie presentato con l'informazione che ha associato a quel cookie 
- Utilizzo dei cookie per: 
	- _autenticazione_ 
	- ricordare profilo utente, scelte precedenti (cfr. “carte-soci”) 
	- in generale creare sessioni sopra un protocollo stateless (es. shopping carts, Webmail) 