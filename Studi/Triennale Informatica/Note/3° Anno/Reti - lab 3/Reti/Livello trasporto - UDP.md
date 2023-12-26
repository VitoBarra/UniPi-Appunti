---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Livello trasporto - UDP
---
è un [[Protocollo]] di [[Livello di trasporto]] con la filosofia best effort
il che non garantisce affidabilità, i messaggi possono essere perduti o consegnati fuori sequenza 

- è orientato al messaggio ovvero
	- nessuna connessione
	- ogni datagramma è indipendente
	- ogni messaggio deve avere dimensione limitate per poter entrare in un unico datagramma UDP, dimensione dipendente dal _MTU_
### Proprietà
- Semplice: non viene gestito lo stato di connessione 
- Intestazioni di 8 byte 
- non si preoccupa del controllo di flusso quindi non si limita nel mandare messaggi
-  Il checksum è _facoltativo_ 
- E' facile e leggero da gestire (non richiede particolari meccanismi) 
- Utilizzato spesso in applicazioni multimediali 
	- _Tolleranza_ piccole perdite 
	- _Sensibilità_ alla frequenza 
- Altri impieghi: [[Livello Applicativo - DNS|DNS]], SNMP (Simple Network Management Protocol)


![[Pasted image 20230106014909.png]]
![[Pasted image 20230106014923.png]]

### Struttura datagramma

![[Pasted image 20230106014945.png]]
- 8 byte di intestazione totale
- _Porta_: numeri di porta della comunicazione (per il demultiplexing è usato solo quello di destinazione). 
- _length_: lunghezza totale (header + dati) del datagramma UDP in byte
	- (16 bit -> max 65535 byte)
- _Checksum_: checksum dell’intero datagramma 
	- E’ opzionale in UDP. 
	- Controllo errore end-to-end 
	- Il pacchetto corrotto viene scartato, ma il mittente non ne riceve notifica 
	- Calcolata sull’intero datagramma UDP più lo pseudo-header (ovvero parte dell’header [[Livello di rete - IP|IP]])
	- ![[Pasted image 20230106015144.png]]
	- Calcolo checksum![[Pasted image 20230106015225.png]]
	- ![[Pasted image 20230106015254.png]]