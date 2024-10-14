---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello Applicativo - MailSMTP
---
è un protocollo di [[Livello Applicativo]]  per la gestione deli scambia di messaggi tra utenti. questo protocollo prende in considerazione che l utente che il destinatario del messaggi potrebbe non essere in grado di ricevere il messaggio al momento del invio si basa quindi su componenti intermediari disaccoppiando lato mittente e destinatario


## Struttura generale
- _User agent_: 
	- per la composizione, editing, lettura di messaggi di posta 
	- es.: Eudora, Outlook, Thunderbird 
- _Mail server_: 
	- i messaggi in entrata ed uscita vengono archiviati sul server 
	- le mailbox (CASSETTE di POSTA) contengono messaggi in ingresso (che devono ancora essere letti) diretti all’utente 
	- una coda di messaggi in uscita (che devono essere inviati)
- _Protocollo SMTP_: dialogo tra mail server
	- “client”: mail server che invia 
	- “server”: mail server che riceve
![[photo_2023-01-04_02-37-03.jpg]]


### Indirizza Email
l indirizzo email che identifica un destinatario è formato da due parti
- _Local part_:specifica la cassetta di posta nel mail server. spesso è identica al nome di login o al nome completo del utente
- _Domain-name_: specifica una mail server. Determina il nome di domino di una destinazione a cui la mail dovrebbe essere recapitata 
![[Pasted image 20230104024051.png]]

## Spoolin: invio del messaggio 
-  L’utente invia un messaggio, il sistema ne pone una copia in memoria (spool – o area di accodamento della posta), insieme con id mittente, id destinatario, id macchina di destinazione e tempo di deposito. 
- Il sistema avvia il trasferimento alla macchina remota. Il sistema (client) stabilisce una connessione TCP con la macchina destinazione 
- Se la connessione viene aperta, inizia il trasferimento del messaggio. 
- Se il trasferimento va a buon fine il client cancella la copia locale della mail 
- Se il trasferimento non va a buon fine, il processo di trasferimento scandisce periodicamente l’area di spooling, e tenta il trasferimento dei messaggi non consegnati. Oltre un certo intervallo di tempo (definito dall’amministratore del server) se il messaggio non è stato consegnato, viene inviata una notifica all’utente mittente.

## Gestion Alias
-  L'alias è una cassetta postale virtuale che serve a ridistribuire i messaggi verso uno o più indirizzi di posta elettronica personali. 
- _molti-uno_: il sistema di alias permette ad un singolo utente di avere identificatori di mail multipli, assegnando un set di identificatori ad una singola persona -> Un utente – più indirizzi postali (es. mansioni)
- _uno-molti_: il sistema permette di associare un gruppo di destinatari ad un singolo identificatore -> Un indirizzo postale – più utenti destinatari (es. mailing list) 
- Meccanismo di espansione degli ALIAS postali: conversione di identificatori di indirizzi postali in uno o più indirizzi postali nuovi 
	- Se l'alias database specifica che all'indirizzo x deve essere assegnato il nuovo indirizzo y, l'espansione dell'alias riscriverà l'indirizzo di destinazione; si provvederà poi a determinare se y specifichi un indirizzo locale o remoto e lo posizionerà nell'area di spool relativa.

![[Pasted image 20230104024315.png]]




### SMTP: Simple Mail Transfer Protocol
l obbiettivo di questo protocolloè l trasferimento affidabile e efficiente dei mail
- è indipendente dal sistema di trasmissione usato
- richiede solo uno stream di byte ordinato e affidabie
- capace di trasportare mail attraverso server intermedi nel percorso da mittente a destinatario finale



inizialmente si stabilisce una connessione bidirezionale tra client e server di posta a cui invia il messaggio che si vuole trasmettere o eventualmente comunica un insuccesso.
successivamente il server SMTP determina l indirizzo di un host che ospita un server SMTP risolvendo il nome utilizzando sistema di  [[Livello Applicativo - DNS|DNS]]. ci saranno altri protocolli che permetteranno al client ricevente di accedere al server contenente il messaggio di cui è destinatario. come POP3 o IMAP
![[Pasted image 20230104025130.png]]


il protocollo utilizza una connessione [[Livello trasporto - TCP|TCP]] con porta 25 per il trasferimento di messaggi affidabile
ha 3 fasi
- _HandShaking_:
	- l client stabilisce la connessione e attende che il server invii 220 READY FOR MAIL (Disponibilità a ricevere posta) Il client risponde con il comando HELO Il server risponde identificandosi A questo punto il client può trasmettere i messaggi
		- ![[Pasted image 20230104030241.png]]
- _trasferimento del messaggio_:
	- Formati da componenti   con caratteri ASCII a 7-bit
		- _Header_ : To:  | From: | Subject:  (_NB: DIVERSI DAI COMANDI INDICATI SOTTO_)
		- _body_: l effettivo messaggio
	- di tipo comando, e hanno una risposta formata da _codice di stato_ e _descrizione_ facoltativa
		- ![[Pasted image 20230104030318.png]]
		- Il comando _HELO_ è necessario affinché il client possa identificarsi (EHLO), utilizzando il proprio nome di dominio, durante la creazione del collegamento. 
		- Il comando _MAIL FROM_ è necessario per indicare il mittente del messaggio e fornire al server un indirizzo e‐mail per eventuali messaggi di segnalazione o di errore. 
		- Il comando  _RCPT TO_ è necessario per indicare il destinatario al mail server a cui viene trasferita la mail (se ci sono più destinatari viene inviato un comando RCPT TO per ciascun destinatario)
- _Chiusura della connessione_


## MINE: Multipurpose Internet Mail Extension
Mine estende il formato delle email per supportare
- Testo in set di caratteri diversi da US-ASCII
- allegati in formato non testuale 
- corpo del messaggi in più parti 
- header in set di caratteri non ASCII
invece di sostituire il formato viene solo esteso, cosi facendo si possono continuare ad utilizzare i mail Server già attivi e lo stesso protocollo ma bisogna cambiare gli user Agent.
- Definisce metodi per rappresentare dati binari in formato ASCII
- Aggiunge linee di intestazione per dichiarare il tipo di contenuti MIME
 ![[Pasted image 20230104030710.png]]
 ![[Pasted image 20230104031431.png]]

#### Forma dei messaggi
- Client e server SMTP si aspettano messaggi ASCII (caratteri ASCII che usano 7 degli 8 bit di un byte). I dati binari usano invece tutti gli 8 bit di un byte (es. immagini, eseguibili, set estesi di caratteri). 
- MIME fornisce vari schemi di transfer encoding, tra cui: 
	- ASCII encoding of binary data: base 64 encoding 
		- Gruppi di 24 bit sono divisi in 4 unità da 6 bit e ciascuna unità viene inviata come un carattere ASCII 
	- Quoted-printable encoding: per messaggi testuali con pochi caratteri non-ASCII, più efficiente 
	- Oggigiorno i mail server possono negoziare l’invio di dati in codifica binaria (8 bit), se la negoziazione non ha successo si usano i caratteri ASCII
![[Pasted image 20230104031735.png]]
![[Pasted image 20230104031746.png]]
in confronto con HTTP il protocollo 

| _HTTP_                                                 | _SMTP_                                                        |     
| ---------------------------------------------------- | ----------------------------------------------------------- | 
| pull                                                 | push                                                        |
| ogni oggetto incapsulato in un messaggio di risposta | tutti gli oggetti di un msg inviati in un multipart message |


## Protocolli di accesso al server Mail
i protocolli di accesso alla posta una volta che questa è arrivata sul server destinatario sono ti tipo  "pull" ovvero sara l utente che adra a richiedere accesso a qui dati

![[Pasted image 20230104133138.png]]

## POP3
Protocollo d accesso al Mail server
- L user agente apre una connessione TCP sulla porta 110 verso il server di posta
- lavora in 3 fasi
	-  _Autorizzazione_
		- comandi del client:
			 - user: specifica la username 
			 - pass: specifica la password 
		 - il server risponde: 
			 -  OK 
			 - ERR 
	  - Fase di scambio comandi del client:
		  - _list_: visualizza la lista dei messaggi 
		  - _retr_: preleva il messaggio per numero 
		  - _dele_: elimina il messaggio dal server 
		  - _quit_: chiude la sessione 
	  - _Aggiornamento_: 
		  - Dopo _quit_ il server cancella i messaggi marcati per la rimozione
### IMAP
un altro protocollo di accesso al server mail
- più feature di POP3
- manipolazione messaggi memorizzati sul server
- comandi per estrarre solo alcuni componenti dei messaggi
## HTTP
usato per l accesso al server mail
	es. HotMail, Yahoo!, Mail, etc.