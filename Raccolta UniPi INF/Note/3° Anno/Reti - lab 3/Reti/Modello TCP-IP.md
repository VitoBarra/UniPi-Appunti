---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3
Status: ToReview
---

Prev: [[Reti - lab 3]]

# Modello TCP-IP
---
il modello TCP/IP è un implementazione dei concetti del [[Modello Stratificato]]
![[Pasted image 20221118015857.png]]
- _applicazione_: supporta le applicazioni di rete, collegamento logico end-to-end: scambio di messaggi tra due processi 
	- ftp, smtp, http 
- _trasporto_: trasferimento dati end-to-end (da un host sorgente all’host destinatario 
	- tcp, udp 
- _rete_: instradamento dei datagrammi dalla sorgente alla destinazione 
	- Ip, ICMP 
- link: trasferimento dati in frame attraverso il collegamento tra elementi di rete vicini – ppp, ethernet, … qualunque cosa 
- _fisico_: trasferimenti dei bit di un frame sul mezzo trasmissivo


vista dei collegamenti logico quindi layer to layer e fisica ovvero i vari passagi che segue il messaggio per arrivare a destinazione
![[Pasted image 20221118015940.png]]

## Incapsulamento
ogni strato aggiunge un header al messaggi che verrà letto dal omologo strato nei nodi intermedi e finali
![[Pasted image 20221118020040.png]]