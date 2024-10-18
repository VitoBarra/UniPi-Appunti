---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello Applicativo - DNS
---
il _Domain Name system_ (DNS) è un sistema del [[Livello Applicativo]].  tutti le altre applicazioni del livello applicativo utilizzano il _DNS_ per cercare i server omologo per il funzionamento


il DNS si occupa di tradurre nomi menomini fatti da stringi di un alfabeto finito in [[indirizzi IP]] che identificano un host univocamente, si utilizza questo formato per garantire l efficienza

## Cenni storici
prima del DNS si utilizzava tenere una associazione statica Nome-Ip in un file host e tutti gli altri periodicamente aggiornavano quel file
oggi con le dimensioni di internet questo è un approccio impraticabile siccome non è possibile mantenere sempre tutti gli host aggiornati con l elenco e non è possibile tenere un elenco cosi grande in modo centralizzato si è quindi passati Al utilizzo del DNS



## DNS

il DNS gira nello strato applicativo e utilizza i livelli sottostanti per il trasferimento dei messaggi.
- utilizza una struttura client server
- non ha un interazione diretta con l utente
![[Pasted image 20230104161214.png]]
le sue responsabilità sono
- Specificare la sintassi dei nomi e le regole per gestirli
- consentire la conversione da nomi a indirizzi e viceversa
fa cio con 
1. Uno _schema di assegnazione dei nomi gerarchico_ e basto su domini 
2. un _database distribuito_ contenente i nomi e le corrispondenze con gli IP implementano con una gerarchia di name server
3. un _protocollo_ per la distribuzione delle informazioni sui nomi tra name server
	- host, router, name server comunicato per risolvere nomi (traduzione nome/ indirizzo)
	- utilizza _UDP_ porta 53 oppure _TCP_
#### Servizi offerti
1. Risoluzione dei nomi ad alto livello in indirizzi IP
2. _Host Aliasing_
	1. un host può avere più nomi uno canonico + tutti gli alias ovvero altri nomi che traducono allo stesso indirizzo ip
3. Mail Server aliasing
	1. Stesso sopra (DA ricontrollare lezione 7 con audio)
4. _Distribuzione del carino_ 
	1. ad un host name posso corrispondere più ip in caso di server distribuiti
	2. il DNS restituisce la lista di Ip variandone l ordinamento e distribuendo cosi il carico al server




## Assegnazione dei nomi
i nomi devono essere univoco con un host o un gruppo di host
con il DNS si definisce una struttura gerarchica  dividendo in parti il nome. ogni parte è separata da un punto e quindi abbiamo qualcosa del tipo
															part1.part2.part3.part4
in questo modo si ha:
- Un assegnazione dei nomi delegabile con un sistema decentralizzato
- Delega del autorità per l assegnazione delle varie parti dello spazio dei nomi questo deve essere univoco
- Distribuzione responsabilità della conversione tra nomi e indirizzi


con questa struttura si genera una gerarchia ad [[Struttura dati - Albero|albero]] dove ogni nodo ha un etichetta di massimo 63 caratteri e la radice ha associata un etichetta vuota  
![[Pasted image 20230104174855.png]]
- Il _Dominio_ è  il sotto albero etichettato dal _nome di dominio_ del nodo radice di quel sottoalbero
- il _nome di dominio_: viene identificato concatenando divisi da un "." le etichette sul percorso dalla radice del albero al nodo radice del _dominio_    
![[Pasted image 20230104175314.png]]

- In Internet i nomi gerarchici delle macchine sono assegnati in base alla struttura delle organizzazioni che ottengono l'autorità per porzioni dello spazio dei nomi 
- La struttura gerarchica permette autonomia nella scelta dei nomi all’interno di un dominio (l’univocità è comunque garantita)
![[Pasted image 20230104181413.png]] 
- Mantenuti da IANA (Internet Assigned Numbers Authority (IANA)


## Gerarchia dei Name Server
nel database il DNS è distribuito e i _Name server_ sono i programmi che accedono a questi database per la conversione dal nome di dominio a indirizzo IP

![[photo_2023-01-04_18-21-41.jpg]]

le informazioni su i domini ripartite su più name server
- _Zona_: regione (tipicamente una parte contigua del albero) di cui è responsabile un name server
- non necessariamente coincide con il dominio
- i Server immagazzinano le informazioni relative alla proprio zona inclusi i riferimenti ai name server dei domini di livello inferiore
![[Pasted image 20230104182306.png]]
### Gerarchia
- _Server Radice_: 
	- Responsabile dei recod della zona radice
	- restituisce le informazioni sui name server dei Top level Domain ovvero di livello 1
- ![[Pasted image 20230104182659.png]]
  - _Server Top-Level Domain_:
	  - Mantiene le informazioni dei nomi di  dominio che appartengono a una certo TLD
	  - Restituisce le informazioni sui name server di competenza dei sottodomini
  - _Server di competenza (authoritative name server)_:
  -  Autorità per una certa zona 
  - memorizza nome e indirizzo IP di un insieme di host 
  - può effettuare traduzioni nome/indirizzo per quegli host 
	  -  Per una certa zona ci possono essere server di competenza primari e secondari
	  -  Server _primari_ mantengono il file di zona 
	  -  Server _secondari_ ricevono il file di zona e offrono il servizio di risoluzione

## Local name server
- Quando un programma deve trasformare un nome in un indirizzo IP chiama un programma locale detto _Risolver_ questo mantiene delle associazioni nome ip se il Risover non è in grado restituire l ip interrogherà un _Local name Server_ se anche lui non è in grado di restituire l IP andrà ad interrogare la gerarchia DNS.
- Il _local name server_ 
	- non appartiene strettamente alla gerarchia dei server
	- ogni [[Struttura di Internet |ISP]] ha un suo _name server locale_ di default 
	-  le query DNS vengono prima rivolte al name server locale che fa quindi da [[Design pattern - Proxy|proxy]]


## Due modi di fare Query DNS

### Iterativa
Query ITERATIVA: 
- Le risposte sono restituite direttamente al client 
- Viene restituito il riferimento al server da contattare successivamente
![[photo_2023-01-04_18-45-08.jpg]]

### Ricorsiva
host www.tintin.fr cerca l'indirizzo IP di www.topolino.it 
1. Contatta il suo DNS locale dns.tintin.fr 
2. dns.tintin.fr contatta il root name server, se è necessario 
3. root name server contatta l'authoritative name server, dns.topolino.it, se è necessario
![[photo_2023-01-04_18-44-37.jpg]]



## DNS: caching ed aggiornamento dei record
una volta che il DNS viene interrogato, alla risposta viene messo in [[Cache]] 
- La cache scade dopo un certo tempo indicato TTL
- i meccanismi di update/notifica sono descritti nella RFC 2136
- migliora il ritardo e riduce il numero di messaggi DNS

### Record DNS
sono i record che contiene il [[DataBase]]  distribuito 
![[Pasted image 20230104185530.png]]


## Protocollo DNS
- UDP porta 52
- permette uso di TCP (per messaggi di grandi dimensioni, tipicamente trasferimenti dati (file di zona) tra server DNS]
- messaggi di query e reply entrambi con lo stesso formato di messaggi 

- ![[Pasted image 20230104190041.png]]
- __Header__:
	- _Identification_: 16 bit-identification questo è uguale per query e risposta
	- _Flags_: se query =0 se Reply =1
- __Body__:
	- _Domande_: campi per il nome richiesto e il tipo di query 
	- _Risposte_: RR nella risposta alla domanda 
	- _Competenza_: record relativi ai server di competenza 
	- Informazioni aggiuntive
