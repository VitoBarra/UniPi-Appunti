---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello Applicativo - FTP
---
è un L _FTP_ o _File transfer protocol_ è un protocollo del [[Livello Applicativo]] 

Server per fare trasferimenti di file da/a un host remoto
utilizza il modello _Client-server_

![[Pasted image 20230104192254.png]]

FTP è lo standard per il trasferimento di file in reti TCP/IP le funzionalità che offre sono:
- il _trasferimento file_: si ottiene una copia locale e si effettuano modifiche e eventualmente si carica la copia locale in remoto
- _Accesso interattivo_: l utente può navigare e cambiare/modificare l aberro di directory nel [[File System]] Remoto
- _Autenticazione_: il client può specificare login e password
- Specifica del formato dei dati da trasferire


## Modello FTP

1. _connessione di controllo_: scambio di comanda e risposte tra client e server. 
2. _Connessione dati_ : Connessione sui cui i dati sono trasferiti con modi e tipo specificati i dati trasferiti possono essere parte di un file, un file o un set di file
3. entrambi usano [[Livello trasporto - TCP|TCP]]
4. è un protocollo _Stateful_
	1. Tiene traccia dello stato del utente come connessioni di controllo associata, directory attuale.


#### FTP: Connessione di Controllo
- il client FTP contatta il Server FTP
	- utilizza un porta casuale e si connette alla porta 21 del Server
- il Client ottiene l autorizzazione sulla connessione di controllo
- il client invia i comandi sulla connessione di controllo 
	- Cambio directory invio file
- La connessioni di controllo è _Persistente_
- La _codifica_ di questa connessione usa la codifica NVT ASCII quella di [[Livello Applicativo - Telnet#Codifica NVT|telnet]]
#### FTP: Connessione dati
- Quando il server riceve un comando per trasferire un file (da o verso il clienti ) sulla connessione di controllo
	1. Il server apre una connessione dati [[Livello trasporto - TCP|TCP]] con il client
	2. Trasferisce l file sulla connessione dati
	3. dopo il trasferimento di file il server chiude la connessione
- é una connessioni non persistente e se ne apre una per ogni trasferimento
##### Data trasfer Mode
-  _Passive_:
	- il client chiede al server di mettersi in ascolto su una porta per una connessioni dati, questo numero viene comunicato sulla _connessione di controllo_  è il client usa la porta comunicata per aprire una nuova connessione (porta di default 20)
-  _Active_:
	- Il server apre una connessione dati TCP con il client
	- il server deve conoscere il numero di porta lato client questo gli la comunica sulla connessione di controllo 
##### Trasmissione
- Per effettuare il trasferimento file, il client deve definire il tipo di file, la struttura dati e la modalità di trasmissione al fine di risolvere i problemi di eterogeneità tra client e server. 
- Il trasferimento file viene preparato attraverso uno scambio di informazioni lungo la connessione di controllo
##### Modalita di trasmissione
- _Stream mode_: FTP invia i dati a TCP con un flusso continuo di bit 
- _Block mode_: FTP invia i dati a TCP suddivisi in blocchi. Ogni blocco è preceduto da un header 
- _Compressed mode_: si trasmette il file compresso
![[Pasted image 20230104194155.png]]


## Comadi di controllo 
![[Pasted image 20230104195403.png]]
![[Pasted image 20230104195412.png]]

## Modello FTP 
![[Pasted image 20230104194344.png]]


>[!note]
>-  Anonymous FTP 
>	- server che supportano connessioni FTP senza autenticazione –
>	-  Tipicamente consentono di accedere solo ad una parte del file system e permettono solo un subset di operazioni (es. no PUT) 
>		- login anonymous 
>		- password guest (o e-mail) 
>- Securing FTP with TLS (FTPS) RFC 4217 
>	- Meccanismo che può essere usato da client e server FTP per implementare sicurezza e autenticazione usando il protocollo TLS (RFC 2246)

