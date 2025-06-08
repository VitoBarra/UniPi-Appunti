---
Course: "[[Reti]]"
topic: nota
tags:
  - RETI_LAB_III
---


# Livello Applicativo - Telnet
---
Telnet è un protocollo del [[Livello Applicativo|Livello Applicativo]]: Protocollo il cui scopo è quello di permettere l'uso interattivo di macchine remote terminale 

Telnet fornisce un servizio _trasparente_ ovvero che fa sembrare al utente di essere direttamente sulla macchina remota offrendo cosi i servizi e i programmi che sono presenti su quella data macchina remota. 

Il suo funzionamento è sulla struttura client-server:
- Un programma _server_ che accetti le richieste
- un programma _client_ che effettua le richieste 
	- interagisce con il terminale utente sul host
	- scambia messaggi con il telnet _server_
		- invia i caratteri inseriti dal utente al server
		- stampa sul terminale I messaggi ricevuto dal server 
- Protocollo TELNET (RCC 854)
	- il _client_ stabilisce con il server una connessione [[Livello trasporto - TCP|TCP]]
	- il _client_ accetta le battute di tasti del terminale e le invia al server. Accetta il caratteri che il server manda indietro e li visualizza sul terminale utente
	- Il _server_ accetta la connessione TCP e trasmette i dati al sistema operativo locale nella macchina serve
- il client si connette alla porta _23_ del server. 
- la connessione TCP persiste per la durata della sessione di login. 
### Login comparison
normalmente con un login locale il sistema operativo assume che gli input  ad un processo vengano forniti della tastiera (standard input ) e che gli output siano inviati al monitor (standard output) 
![[Pasted image 20230103225053.png]]

con telent e il login remoto gli input  dati al terminale vengono mandati al client TELNET che li invierà sulla rete e saranno ricevuto dal server TELNET che li inviera ad uno _pseudo-terminal Driver_  
![[Pasted image 20230103225327.png]]
- _Pseudo terminale Driver_: entry point del sistema operativo che consente di trasferire caratteri a un processo come se provenissero dal terminale. Ha il compito di accettare i caratteri dal server Telnet e trasmetterli al sistema operativo. Il sistema operativo consegna i caratteri all’applicazione opportuna

## Telnet: NVT
TELENT deve assicurare di poter essere utilizzato con i magio numero di [[Sistemi Operativi]] ma questo può essere difficile siccome va affrontato il problema della compatibilità dei  terminali che possono differire gli uni dagli altri per:
- il set e codifica di caratteri ([[Conoscenze informatiche - Charset|caharset]])
- la larghezza della linea e lunghezza della pagina
- i tasti funzioni individuati da diverse sequenze di caratteri (_escape sequence_)
- es. diversa combinazioni di tasti per interrompere un processo (CTRL-C,ESC) , caratteri ASCII diversi per terminazione righe di testo

per risolvere questo problema  si definisce un terminale virtuale detto __NVT__, interpretato un con terminale astratto che funge da terminale "franco" tra i due.  il protocolla assume si attivo sia su server che su client. questo definisce un [[Conoscenze informatiche - Charset|Charset]] e delle funzionalità predefinite, cosi da poter scambiare i messaggi senza preoccuparsi della differenza dei terminali.  

per l utilizzo il terminale del l utente invia i messaggi al client TELNET  con il proprio charset, questo lo traduce nel charset di NVT e invia il messaggi al server TELNET a questo punto avviene un altra traduzione dal charset di  NVT al charset del terminale locale del server
![[Pasted image 20230103225950.png]]

#### Codifica NVT
i terminale _NVT_ si scambiano messaggi a 7-bit UI-ASCII, ogni carattere p inviato come ottetto
- 1 bit = 0: se caratteri
- 1 bit = 1: se comandi


>[!note]
>TELENT non è sicuro passa le password in chiaro si dovrebbe preferire l utilizzo di [[Livello Applicativo - SSH|SSH]]

