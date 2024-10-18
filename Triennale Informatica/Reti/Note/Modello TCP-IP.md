---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
Status: ToReview
---

Prev: [[Reti]]

# Modello TCP-IP
---
il modello TCP/IP è un implementazione dei concetti del [[Modello Stratificato]]
![[Pasted image 20221118015857.png]]
- _applicazione_: supporta le applicazioni di rete, collegamento logico end-to-end: scambio di messaggi tra due processi 
- _trasporto_: trasferimento dati end-to-end (da un host sorgente all’host destinatario 
- _rete_: instradamento dei datagrammi dalla sorgente alla destinazione 
- _link_: trasferimento dati in frame attraverso il collegamento tra elementi di rete vicini  
- _fisico_: trasferimenti dei bit di un frame sul mezzo trasmissivo


vista dei collegamenti logico quindi _layer-to-layer_ e fisica ovvero i vari passaggi che segue il messaggio per arrivare a destinazione
![[Pasted image 20221118015940.png]]

## Incapsulamento
ogni strato aggiunge un _header_ al messaggi che verrà letto dal omologo strato nei nodi intermedi e finali
![[Pasted image 20221118020040.png]]