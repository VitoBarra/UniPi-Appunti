---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello di rete - IP
---

è un [[Protocollo]] di [[Livello di rete]]

## Introduzione
- è di tipo connection-less
	- non ci sono connessione logiche tra mittenti e destinatario
- best-effort
	- quindi nessuna garanzia che i pacchetti vengano ricevuto nel rodine in cui sono stati inviati
	- non è garantita la consegna
- non affidabile
	- Nessun meccanismo di recupero se un pacchetto è perso
- nessuna garanzia sulla qualità dei servizio
	- nessuno controllo di flusso
	- nessun limite sul tempo di consegna


## Servizi
#### Forwarding
trasferimento del pacchetto sull’appropriato collegamento di uscita
![[Pasted image 20230106194734.png]]
#### Instradamento 
processo decisionale di scelta del percorso verso una destinazione (algoritmi di instradamento o routing)
![[Pasted image 20230106194901.png]]

## Formato Datagramma
![[Pasted image 20230106195106.png]]
![[Pasted image 20230106195117.png]]
- _Versione_ (4 bit): specifica la versione di IP usata (attualmente IPv4 o IPv6) 
- _Hlen_ (lunghezza dell'header, 4 bit): lunghezza dell'intestazione espressa in parole da 32 bit. Tipicamente vale 0101 ovvero 20 byte. 
- _Tipo di servizio_ (8 bit): serve per “colorare” il datagramma IP (basso ritardo, affidabilità, ecc...). Inizialmente Type of Service, poi : 
	- 6 bit per _Differentiated Services_ 
		- I pacchetti vengono marcati in base alla classe di servizio (telefonata, controllo, multimedia streaming, dati a bassa priorità) 
		- Differenti politiche di accodamento ai router 
	- 2 bit _Explicit Congestion Notification_ (ECN) – supporto a livello rete e trasporto per la notifica di eventi di congestione usati nel [[Livello trasporto - TCP|TPC]]
- _Lunghezza del datagramma_ (16 bit): è la lunghezza di tutto il datagramma in byte, header incluso. 
	-  Dim. Max 65535 byte (nella pratica 1500 byte) 
- _Identificatore, flag, offset_: sono campi per la frammentazione  
- _Tempo di vita_ (8 bit): ad ogni passaggio da un router viene decrementato, quando raggiunge lo zero viene scartato. Assicura che eventuali percorsi ad anello non provochino traffico perpetuo nella rete 
	- Valore iniziale dipende dal [[Sistemi Operativi|sistema operativo]]: esempi 30, 64, 128, 255
- _Protocollo_ (8 bit): in ricezione all’host destinatario indica quale protocollo dello strato superiore deve ricevere i dati. Inizialmente la tabella era nella RFC1700 (STD2), attualmente è un database online che si trova su iana.org 
	- Demux, es. TCP 6, UDP 17 
- _Checksum dell'intestazione_ (16 bit): viene calcolato il checksum della sola intestazione (ponendo questo campo pari a zero) ad ogni router (il TTL cambia ad ogni hop!). Se si ottiene un errore si scarta il datagramma.
• _Indirizzi sorgente e destinazione_ (32 bit): indirizzi IP del mittente e del destinatario. 
- _Opzioni_ (lunghezza variabile, multiplo di 32 bit): uso sporadico, da 0 a 40 byte 
- _Dati_: dati trasportati dal datagramma IP.

>[!question]
>Approfondimento suggerito Determinare per quale motivo UDP e TCP si preoccupano di controllare l’integrità di informazioni di livello network se anche IP usa una sua checksum.
## Frammentazione
#### a cosa serve
la dimensione massima del datagramma IP deve essere incluso nel _MTU_ 
-  _MTU_: la quantita massima di dati traportata dal  [[Livello di collegamento]] in un singolo frame 
![[Pasted image 20230106200951.png]]
l _MTU_ puo variare a seconda del collegamento e se il datagramma supera l _MTU_ allora c è bisono della frammentazione di quel datagramma per poterlo spedire

##### Meccanismo di frammentazione 
1. Se il router riceve un datagramma la cui dimensione supera l’_MTU_ della rete verso cui deve inoltrare quel datagramma, il router frammenta il datagramma IP in due o più datagrammi più piccoli, detti frammenti. 
2. Il riassemblaggio viene effettuato dall'entità rete nel sistema terminale (destinazione). 
	1. Se anche solo un frammento non arriva a destinazione si butta tutto il datagramma
##### inoltro dei frammenti
1. ogni frammento è un datagramma IP completo e vengono trasmessi indipendentemente 
2. se serve i messaggi posso essere frammentati ulteriormente 
![[photo_2023-01-06_20-17-56.jpg]]


#### Gestione arrivi di frammenti
![[Pasted image 20230106200227.png]]
- i frammenti potrebbero arrivare in ordine sparso non c è garanzia arrivino in ordine
- per ricomporre il messaggi originale si usano: 
	- _Identificatore_ (16 bit) è associato al datagramma dall’host sorgente. Associato a IP sorgente e IP destinazione identifica quel datagramma in un intervallo di tempo ragionevolmente lungo. 
		- tutti i frammenti di un datagramma hanno lo stesso identificatore 
	- _Offset_ (13 bit): indica la posizione relativa come multiplo di 8 byte. Serve ad ordinare i frammenti nell’assemblaggio. 
		- I frammenti devono essere multipli di 8 byte 
		- Primo frammento Offset =0 
	- _Flag_ (3 bit) serve ad identificare l’ultimo frammento 
		- Il bit 0 è riservato (per ora vale sempre 0) 
		- Il bit 1 _do not fragment_ vale: 
			- 0 se il pacchetto può essere frammentato 
			- 1 se il pacchetto non deve essere frammentato 
		- Il bit 2 _more fragments_ vale: 
			- 0 se il pacchetto è l’ultimo frammento 
			- 1 se il pacchetto non è l'ultimo frammento

> [!note]
> Frammentare è un processo critico 
> - puo introdurre ritardi di elaborazione
> - se un solo frammento manca si butta via tutto il messaggio
>
> per evitare questi problemi si evita la frammentazione
> - do not frament in Ipv4
> - Ipv6 non supporta la frammentazione 



## Instradamento
#### IPv4
-  Ogni host è connesso ad Internet attraverso un'interfaccia di rete, che è il confine fra l'host ed il collegamento su cui vengono inviati i datagrammi. 
	- Ad ogni interfaccia è assegnato un indirizzo IP. 
	- I router devono necessariamente essere connessi ad almeno due collegamenti. 
- Gli indirizzi IP sono costituiti da 32 bit (4 byte), rappresentati in notazione decimale puntata.
![[Pasted image 20230106213243.png]]
 Ogni host ha un indirizzo univoco diviso in due parti: 
  - _Network ID + Host ID_ , che identificano una rete IP su Internet e l’host su quella rete IP.
  - ![[Pasted image 20230106224319.png]]

Questo porta a dover scegliere come assegnare gli indirizzi
##### Classfull addressing
![[Pasted image 20230106224425.png]]
-  5 classi di indirizzi IP 
- _Classe A_: 7 bit per 128 reti IP, 24 bit 
	- 0.0.0.0 - 127.255.255.255 
	- Reti di 16 milioni di host 
- _Classe B_: 14 bit per ca. 16000 reti IP, 16 bit host id 
	- 128.0.0.0 - 191.255.255.255 
	- Reti di circa 64000 host 
- _Classe C_: 21 bit per reti IP e 8 bit per host id 
	- 192.0.0.0 - 223.255.255.255 
	- Reti di circa 256 host 
- _Classe D_, riservata a multicasting, 
	- 224.0.0.0 - 239.255.255.255 
- _Classe E_, riservata per usi futuri 
	- 240.0.0.0 – 255.255.255

##### classles addressing 
più flessibile rispetto al classfull Addressign
![[Pasted image 20230106225423.png]]![[Pasted image 20230106225438.png]]Una rete con un prefisso di rete di n bit può avere al massimo $2 ^{32-n} -2$ host (devo sottrarre indirizzo di rete e indirizzo di broadcast)

##### Subnet mask
una siringa di 32 bit di cui i primi $n$ a 1, utile per ottenere solo l indirizzo di rete facendo l AND con l indirizzo IP 
![[Pasted image 20230106225751.png]]

### Indirizzi speciali
- _This-host_ 0.0.0.0 
	- Usato quando un host ha necessità di inviare un datagramma ma non conosce il proprio indirizzo IP (indirizzo sorgente) 
- _Limited-broadcast_ 255.255.255.255 
	- Usato quando un router o un host devono inviare un datagramma a tutti i dispositivi che si trovano all’interno della rete. I router bloccano la propagazione alla sola rete locale. 
- _Loopback_ 127.0.0.1 
	- il datagramma con questo indirizzo di destinazione non lascia l’host locale (localhost). Per test e debug. 
- _Indirizzi privati_ 
	- Quattro blocchi riservati per indirizzi privati (riservati per reti locali): 
	- 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16, 169.254.0.0/16 
- _Indirizzi multicast_  Blocco 224.0.0.0/4


## inoltro (Forwarding)
ogni datagramma IP deve essere inoltrato 
- _Inoltro diretto_: Se il pacchetto IP ha come destinatario un host che è nella rete di chi inoltra 
	- l invio è diretto al destinatario
	- l indirizzo di destinazione a [[Livello di collegamento]] è quella del destinatario (MAC address)
	- non viene interpellata nessun altra entita
- _Inoltro indiretto_: il pacchetto IP ha come destinazione un host di un'altra rete (o subnet) IP
	- viene delegato l invio ad un _router_
	- l indirizzo di destinazione a [[Livello di collegamento]] e quello del _router_
Per far sei che entrambi questi due casi siano fattibili devono essere vere due cose 
1. c è un cammino diretto, a livello data-link tra tutti gli host che appartengono alla stessa sottorete
2. ogni host coinvolto abbia un indirizzo IP ben formato 


#### Router
![[Pasted image 20230107001213.png]]
![[Pasted image 20230107001229.png]]
- Aggrego gli indirizzi di inoltro cambiando il numero di bit della parte di rete 
![[Pasted image 20230107001242.png]]
- in questo caso ordino gli indirizzi partendo dalla netmask piu lunga
- per inoltrare il pacchetto vado in ordine per scegliere
![[Pasted image 20230107001258.png]]
 - Divisione di Ip associati in più router

##### NAT
in casi di reti private che vogliono comunicare con esterno c è bisogno un router NAT, questo deve avere almeno un IP pubblico.
- tutto il traffico in uscita dalla rete privata verso l esterno avrà come IP Sorgente l IP pubblico NAT
- tutto il traffico in entrata dalla rete pubblica verso l interno avrà come IP Sorgente l IP pubblico NAT
![[Pasted image 20230107001702.png]]
il Router mantiene una tabella di traduzione per reindirizzare i pacchetti nella rete privata.

bisogna cambiare la porta nella traduzione siccome i messaggi arrivano da più host e potrebbero avere la stessa porta cambiando la porta se ne può assegnare una per comunicazione garantendone l univocità

>[!Question]
>Quante comunicazioni può gestire un router NAT con un solo indirizzo pubblico?
>credo il numero massimo di [[Interfaccia Socket#Identificare un processo|porte]] quindi $2^{16}$

## IPv6
Motivazioni del protocollo IPv6
-  Esaurimento indirizzi a 32 bit 
	- indirizzi a 128 bit 
- Velocizzare elaborazione e forwarding pacchetti 
	- lunghezza fissa (40 byte) dell’header 
	- eliminato checksum 
- Risparmiare ai router costo frammentazione 
	- ICMPv6: msg “packet too big” (sorgente deve preoccuparsi della frammentazione) 
- Facilitare QoS 
	- introdotta “flow label” per identificare datagram appartenenti allo stesso “flow”
	- (p.e. insiemi di pacchetti che richiedono un trattamento speciale come QoS p.e. audio video, high-priority traffic)
![[Pasted image 20230109004557.png]]