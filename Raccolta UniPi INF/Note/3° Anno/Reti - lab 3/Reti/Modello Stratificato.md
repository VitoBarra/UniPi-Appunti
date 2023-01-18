---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3
Status: ToReview
---

Prev: [[Reti - lab 3]]

# Modello Stratificato
---
il modello stratificato è un insieme di [[Protocollo|protocolli]] organizzati su livelli. per la gestione di nodi di una [[Reti Concetti Generali|Rete]]

## Obbiettivi
1. _Efficienza_: minimizzare lo sforzo globale di consegnare le lettere (non la singola!) 
2. _Efficacia_: consegnare la maggior quota possibile di lettere
## Specifiche
- costituito da sistemi di consumatori/produttori
- sistemi organizzati in strati funzionali (livelli) 
- ogni strato fornisce servizi allo strato superiori e usa i servizi di quello inferiore 
- ogni strato scambia informazioni direttamente solo con gli strati adiacenti 
- in ogni comunicazione i due strati omologhi svolgono funzioni reciproche 
- esistono sistemi (intermedi) che implementano solo alcune funzioni
## Vantaggi 
- scompone il problema in sotto problemi più semplici da trattare 
	- quindi il singolo strato è più semplice del sistema nel suo complesso 
	- Semplificazione della progettazione, implementazione e manutenzione del software 
- i vari livelli sono indipendenti posso quindi modificare l’implementazione di uno strato senza dover cambiare gli altri strati (adiacenti e non), a patto che l’interfaccia non cambi 
	- I servizi forniti dagli strati inferiori possono essere usati da più entità negli strati adiacenti superiori 
- definendo solamente servizi e interfacce, i livelli diversi possono essere sviluppati da soggetti diversi
- Ogni livello logico di astrazione è realizzato in un apposito strato 
	- Un livello viene creato quando si rende necessario un diverso grado di astrazione 
- Ogni strato svolge una sola e ben definita funzione ([[Separation of Concern]])
- Il flusso dati attraverso le interfacce di ogni strato deve essere minimizzato               
	([[Information Hiding]])  
- Il numero degli strati deve essere minimizzato, compatibilmente con la loro complessità 
	- Numero sufficientemente alto per garantire che nessun livello sia troppo complesso e contenga troppe funzioni, ma anche sufficientemente basso per non rendere troppo onerosa l’integrazione e l’architettura poco flessibile


