---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
Status: ToReview
---

Prev: [[Reti]]

# Modello ISO-OSI
---
il modello Iso/osi è un implementazione dei concetti del [[Modello Stratificato]]
![[Pasted image 20221118010357.png]]
nell collegamento tra end systems
![[Pasted image 20221118013620.png]]

gli strati dal 7 al 5 sono strati applicativi realizzati per l interazione con l utente mentre  i sottostanti strati sono di supporto alla rete e alla infrastruttura trasmissiva 

## Modalita di servizio
1. connection-oriented:
	- Associazione logica tra due o più sistemi al fine di trasferire dati 
	- Gestione della connessione:  
		- Instaurazione della connessione 
		- Trasferimenti dei dati 
		- Chiusura della connessione 
	- Connection-less 
		- I dati vengono trasferiti senza stabilire una connessione
## Flusso di informazione
- Per la rete, l'informazione ha origine al livello Applicativo 
- L'informazione discende i vari livelli fino alla trasmissione sul canale fisico 
- Ogni livello aggiunge all’informazione del livello superiore una propria sezione informativa (o più di una) 
	- header che contiene informazioni riguardanti esclusivamente quel livello. 
- Per i dati ricevuti si segue il cammino inverso
- processo di incapsulamento delle informazioni 
	- ogni livello esegue una operazione di incapsulamento su dati già incapsulati dal livello precedente 
	- Processo reversibile 
- la definizione dell'incapsulamento è tale da garantire la possibilità di estrarre i dati precedentemente incapsulati

## Incapsulamento
_Header_: Qualificazione del pacchetto dati per questo livello 
_DATA_: Payload proveniente dal livello superiore 
_Trailer_: generalmente usato in funzione di trattamento dell'errore (rivelazione, correzione)
![[Pasted image 20221118014514.png]]
![[Pasted image 20221118014523.png]]