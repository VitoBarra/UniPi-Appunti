---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Peer-to-Peer
---
architettura di connessione tra utenti dove ogni nodo fa sia da serve che da client sono tutti nodi pari (peer)

### Problemi
coppie di peer che economica tra loro
- non necessariamente sempre attivo
- un nodo può cambiare  indirizzo IP ogni volta che si connette 


### Directory centralizzata
implementata da _Napster_
![[Pasted image 20230113172232.png]]
1. alla connessione del utente manda il proprio IP e i metadati dei file che possiede
2. un secondo nodo che vuole quei dati chiede al server a quale peer richiedere quelle risorse
3. avviene l effettiva connessione _peer to peer_
##### Problemi 
- unico punto fallimento (si possono duplicare i server)
- collo di bottiglia per performance
- facile da "oscurare"


### Reti decentralizzate peer-To-Peer

#### Reti non strutturate
##### Query flooding
Implementato da _Gnutella_
- completamente distribuita
- 
![[Pasted image 20230113173058.png]]
1. ogni nodo che bisogno di una risorsa invia una query a tutto i suoi vicini
2. _if_ hanno la risorsa rispondono direttamente al host che l ha richiesta 
3. _else_ inoltrano la richiesta a tutti i proprio vicini
##### problematiche
- Flooding
- poco scalabile


##### Copertura Gerarchia
- Approccio misto tra flooding e Server
- Ogni peer o 
	- è _group leader_ (se “potente” in banda o risorse) 
	- viene assegnato ad un group leader 
- Connessioni [[Livello trasporto - TCP|TCP]] 
	- tra peer e il suo group leader 
	- tra (alcune) coppie di group leader
![[Pasted image 20230113173924.png]]
Ogni file associato con un suo hash e un suo descrittore 
- Client invia una query di keyword a suo group leader 
- Group leader risponde con dei “match” del tipo 
	- _< hash del file, indirizzo IP >_
- Se il leader inoltra la query ad altri leader, questi rispondono con altri match 
	- Il cliente sceglie quindi i file da scaricare 
- _Protocollo per gestire disconnessione dei group leader_: i peer di quel group leader devono essere assegnati ad un altro group leader
##### Problematiche
- più complesso
- necessario protocollo per la gestione di ingresso e uscita dalla rete

#### BitTorrent
_Tracker_: il nodo che coordina la distribuzione del file 
Per condividere un file, un peer crea un file _.torrent_, che contiene metadati sul file condiviso e sul _tracker_
![[Pasted image 20230113175433.png]]
-  Nuovo peer 
	- cerca (con motore ricerca) "Do what you u want" e ottiene un file _.torrent_, ovvero un metafile con info sui _chunk_ e indirizzo IP di tracker 
	- contatta tracker e riceve indirizzi di alcuni _peer_ dello _swarm_ ovvero degli host che stanno condividendo quella risorsa

- ##### Strategie principali 
- "_tit for tat_" (pan per focaccia): inviare dati ai peer che inviano dati, scegliendo quelli che stanno inviando dati a frequenza maggiore 
- Ciascun peer scambia dati con al più 4 vicini 
	- Priorità ai vicini che stanno inviando dati alla velocità più alta
		- per promuovere chi sta condividendo e penalizzare comportamenti _egoistici_
- Ogni peer classifica i suoi vicini in "soffocati"(choked) e "interessati"(interested) 
	- aggiorna ogni 10 sec la sua classifica 
	- ogni 30 sec sceglie un choked a caso e lo promuove 
		- fatto cosi che i nuovi arrivati possono entrare nella rete 
- “_rarest (chunks) first_” ( cosi diventano anche meno “rari”)
	- il client che li riceve è più sicuro che quei dati riesca ad ottenerli
	- fornisce più in fretta ridondanza alla rete
#### Reti Strutturate
1.  Vincoli sul grafo (strutturato) e sul posizionamento delle risorse sui nodi del grafo 
	1. L’organizzazione della rete segue principi rigidi 
2. L’aggiunta o la rimozione di nodi è un’operazione costosa 
3. Obiettivo: migliorare la localizzazione delle risorse 
	1. Esempi: Chord, Pastry, CAN


##### DHT: Distributed Hash Table 
- Ad ogni peer è assegnato un _ID_ ed ogni peer conosce un certo numero di peer 
- Ad ogni _risorsa condivisa_ (pubblicata) viene assegnato un _ID_, basato su una funzione hash applicata al contenuto della risorsa ed al suo nome 
- Routing della risorsa pubblicata verso il peer che ha l’ID più «vicino» a quello della risorsa 
- La richiesta per la risorsa specifica sarà instradata verso il peer che ha l’ID più «vicino» a quello della risorsa
- _vicino_: secondo metriche di lontananza
- piu difficile da gestire da gestire le uscite e le entrate