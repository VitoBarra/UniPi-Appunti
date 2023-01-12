---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3 MOC]]

# Livello di trasporto
---
il livello di trasporto è uno livello del [[Modello TCP-IP]] e realizza la _comunicazione logica_  fra __processi__ residenti un host system diversi. 
- Per _logico_ si intende che i processi si comportano come se fosse direttamente collegati senza preoccuparsi dei dettagli della comunicazione fisica usata per la comunicazione
- questo Strato offre servizi allo strato applicazione
	- L applicazione con queso strato per ricerve e trasmettere dati, questa scegli lo stili di comunicazione ad esempio sequenza di  _messaggi singolo _o _sequenza contina di byte_. i programma applicativo passa i dati nela forma richiesta al livello di trasporto per la consegna
- Utilizza i servizi dell [[Livello di rete]]
	- il livello di rete mette in comunicazione gli Host non i Processi
- ![[Pasted image 20230105012537.png]]

![[Pasted image 20230105012718.png]]![[Pasted image 20230105012759.png]]

## Servizi offerti
- controllo degli errori (Header+dati)
- #### Demultiplexing
	- lo strato trasporto provvede allo smistamento dei pacchetti fra la rete e la applicazioni
- #### Multiplexing
	- lo strato trasporto provvede all accorpamento dei flussi dati dei processi verso la rete, lo fa aggiungendo a i dati ricevuto dallo strato superiore un preambolo 
- ![[Pasted image 20230105013008.png]]

## Demultiplexing
l  host riceve  una datagramma questo ha indirizzo IP sorgente in Ip destinatori. il datagramma contiene un segmento di livello di trasporto
![[Pasted image 20230105013537.png]]
ogni segmento contiene nel header il numero di prota della sorgente e il numero di porta del destinatario.

> [!note]
>la comunucazione di trasporto  TCP o UDP è identificata in maniere univaca grazei alla coppie numeri Ip/porta
>- La _porta_ è un numero di 16 bit usigned (0-65535) che viene assegnato un processo o vero ad un punti di demultiplexing dei protocolli [[Livello trasporto - TCP|TCP]] o [[Livello trasporto - UDP|UDP]]
>- l _indirizzo IP_ è unn indirizzi di 32 bit presente nello stacp [[Modello TCP-IP|TCP/IP]]
>
>
>Per standard ci sono dei range di porte 
>-  _System Ports_ (Well Known Ports): da 0 a 1023, assegnate da IANA, identificano processi server 
>- _User Ports_ (o Registered Ports): da 1024 a 49151, assegnate da IANA 
>- _Dynamic Ports_ (Private o Ephemeral Ports), non assegnate da IANA 
>il [[Sistemi Operativi|Sistema operativo]] assegna dinamicamente le porte ai processi che ne fanno richiesta

#### Demultiplexing senza connessione - UDP
- Socket UDP identificata dalla coppia _(IP, porta)_
- Lo strato di trasporto dell'host ricevente consegna il segmento UDP alla socket identificata da IP e porta destinazione 
- I datagrammi con IP e/o porta _mittente differenti_ ma _stessi IP e porta destinatari_ vengono consegnati alla stessa socket
![[Pasted image 20230105014750.png]]
#### Demultiplexing con connessione - TCP
La socket TCP connessa è identificata da 4 parametri: 
- Indirizzo IP/Numero di porta di origine 
- Indirizzo IP/ Numero di porta di destinazione

L'host ricevente usa i 4 parametri per inviare il segmento alla socket appropriata 
- Un host server può supportare più socket contemporanee 
- Es. server Web: socket differenti per ogni client
![[Pasted image 20230105014848.png]]
