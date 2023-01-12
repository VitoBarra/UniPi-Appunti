---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3 MOC]]

# Livello di collegamento
---
il livello di collegamento è un livello del [[Modello TCP-IP]] 

fornisce un servizio al  [[Livello di rete]]
![[Pasted image 20230109010355.png]]
gestisce l invio di messaggi tra i nodi adiacenti
i collegamenti tra i nodi possono essere di diversa natura 
- Cablati
- Wireless
Il livello di collegamento lavora con _Frame_ o _Trama_

##### Divisibili in macro categorige:
- _Punto punto_: 
	- WAN, LAN eethernet
- _Broadcast_:
	- collegamento condiviso tra piu dispostivi, quando un nodo trasmette un frame, il canale lo diffondo a tutti gli altri nodi revono una copia
	- Wirless LAN, reti satelliatari, Ethernet.

##### Diviosne in sottolivelli:
1. _Data-Link Control_:
	- Framing
	- Flow and error Control
2. _Medium accesso control_
	- Accesso al mezzo (in brodcast possono esserci collisioni)
	- Regola per accedere al mezzo


##### Servizzi offerti
- _Framing_: 
	- I protocolli incapsulano i datagrammi del livello di rete all’interno di un frame a livello di link. 
	- Frame: campo dati, intestazione e eventuale trailer 
	- Il framing separa i vari messaggi durante la trasmissione da una sorgente a una destinazione 
	- Per identificare origine e destinatario sono utilizzati indirizzi di livello collegamento (diversi rispetto agli indirizzi IP!) 
- _Consegna affidabile_:
	- È considerata non necessaria nei collegamenti che presentano un basso numero di errori sui bit (es. fibra ottica, cavo coassiale e doppino intrecciato) 
	- È spesso utilizzata nei collegamenti soggetti a elevati tassi di errori (es.: collegamenti wireless)
- _Controllo di flusso_:
	- Evita che il nodo trasmittente saturi quello ricevente. 
- _Rilevazione degli errori_: 
	- Gli errori sono causati dall’attenuazione del segnale e da rumore elettromagnetico.
	- Il nodo ricevente individua la presenza di errori 
	- è possibile grazie all’inserimento, da parte del nodo trasmittente, di bit di controllo di errore all’interno del frame. 
- _Correzione degli errori_:
	- Il nodo ricevente determina anche il punto in cui si è verificato l’errore, e lo corregge.



#### Implementazione Livello di collegammento 
la proprozione puoi dipendere dalla _Network interface card_ (NIC) ma generalmente sono sia su hardware che software. in particolare la correzione degli errori 
![[Pasted image 20230109021430.png]]


### Mezzo condiviso
in mezzo condiviso tutto mandano messaggi sul mezzo ma se posso avvenire dello _collisione_ che posso corrompere il messaggio
- _Collisione_ : se un nodo riceve due o più segnali nello stesso istante
Ci sono vari algoritmi per gestire i mezzi condivisi e le collisioni.

Idealmente :
_dato_: canale broadcast con rate R bps desiderata: 
1. Quando un solo nodo trasmette, può inviare dati con un rate di R bps. 
2. quando M nodi vogliono trasmettere, ciascuno trasmette ad un rate medio R/M 
3. decentralizzato 
	1. Non ci sono nodi speciali che coordinano la trasmissione 
4. semplice

##### Classi di protocolli:
-  _suddivisione del canale_ :
	- Dividono il canale in “pezzi” (risorse) più piccoli (time slot, frequenza, codice) – La risorsa è allocata al nodo in modo esclusivo 
- _ad accesso random_: 
	- Il canale è condiviso, possono esserci collisioni 
	- meccanismi per “ recuperare ” da eventi di collisione 
- _a rotazione_: 
	- Rotazione tra i nodi _turni_ 


## Algoritmi

### _suddivisne del canale_ 
#### TDMA: time division multiple access
ogni stazione ha a disposizione in time slot di lunghezza fissa.
![[Pasted image 20230109022522.png]]
cosi facendo non ci sono interferenze
##### Contro
- Se una stazione non parla il suo time slot viene sprecato e il mezzo è inutilizzato
#### FDMA: frequency division multiple access
- canale divisi in frequenze 
- ad ogni stazione è assegnata una banda di frequenza fissa 
- ![[Pasted image 20230109022833.png]]
##### Contro
- Se non si inviano messaggi le frequenze libere non vengono usate e si sta quindi sfruttando meno il mezzo
### _Random_
- quando un nodeo deve inviare dati li invia
	- trasmette al massimo rate del canele 
	- non c è coordinamento
	- se ci sono _collisioni_ Si cerca di recuperare
#### ALOHA
_assunzioni_: 
- time diviso in slot uguali e fissi 
- I nodi iniziano a trasmettere all’inizio dello slot 
- I nodi sono sincronizzati 
- se 2 o più nodi trasmettono, ogni nodo rileva la collisione

_funzionamento_: 
- Quando il nodo deve trasmettere un frame, comincia a trasmetterlo all’inizio dello slot successivo 
- Se non ci sono collisioni: il nodo può inviare un nuovo frame nello slot successivo 
- Il nodo rileva una collisione: il nodo ritrasmette con probabilità $p$ il frame nello slot successivo finché la trasmissione non ha successo
	- in pratica sceglie a random se rimandare il pacchetto il prossimo slot e si spera di di trovare il mezzo libero
![[Pasted image 20230109023410.png]]
##### Contro
- collisioni, spreco di slot 
- Se c’è un gran numero di nodi attivi canale usato con successo solo il 37% del tempo
##### pro
- semplice
- _Fortemente decentralizzato_: devono essere sincronizzati solo gli slot 
- Il singolo nodo attivo può trasmettere alla massima velocità consentita dal canale 
#### ALOHA unslotted
- Più semplice:
- non serve la sincronizzazione 
- Quando il nodo ha dati da inviare  li trasmette immediatamente 
- Probabilità di collisione maggiore rispetto allo slotted Aloha funzione circa la meta peggio 
- Un frame inviato a $t0$ collide con altri frame inviati nell’intervallo [t0 -1,t0 +1]
![[Pasted image 20230109023509.png]]

#### carrier sense multiple access: CSMA
- Se il canale è libero inizia a trasmettere
- se il canale è occupato, ritarda la trasmissione
anche aspettando siccome c è ritardo di propagazione comuque ci potrebbero essere delle collisioni 
- In questi casi la trasmissione è persa e bisogna ritrasmettere
![[Pasted image 20230109024438.png]]
#### CSMA/CD (Collision detection)
come il CSMA normale ma se si nota la collisione si annulla la trasmissione per evitare di sprecare ulteriormente il canale
![[Pasted image 20230109024202.png]]
1. NIC receives datagram from network layer, creates frame 2. If NIC senses channel idle, starts frame transmission. If NIC senses channel busy, waits until channel idle, then transmits. 3. If NIC transmits entire frame without detecting another transmission, NIC is done with frame! 4. If NIC detects another transmission while transmitting, aborts and sends jam signal 5. After aborting, NIC enters binary (exponential) backoff: – after mth collision, NIC chooses K at random from {0,1,2, …, 2m-1}. NIC waits K·512 bit times, returns to Step 2 – longer backoff interval with more collisions

### _Rotazioni_
#### Polling
- Nodo master che invia il permesso di parlare ad un nodo slave
![[Pasted image 20230109024640.png]]
##### Contro
- overhead per il flusso di controllo


#### TokenRing
puo parlare solo chi ha il token che gira per la topologia della rete
![[Pasted image 20230109024738.png]]
##### Contro
- overhead per l invio del token che non necessariamente deve parlare


