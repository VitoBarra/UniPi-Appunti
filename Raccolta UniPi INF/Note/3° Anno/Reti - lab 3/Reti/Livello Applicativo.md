---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Livello Applicativo
---

Il livello applicato è uno strato del modello [[Modello Stratificato]] che rappresenta le applicazioni ed è il livello più alto. le applicazioni sono dette applicazioni di rete queste sono distribuiti su più host terminali.
I livelli applicazioni nei due lati della comunicazione si comportano come si esistesse un collegamento diretto, questo è un collegamento logico che astraete su tutto il sistema sottostante. 
![[Pasted image 20230102180819.png]]
### Protocolli
I protocolli sono le regole di comunicazione che utilizzati dalle applicazioni per funzionare
- Definisce _i tipi_ di messaggi scambiati (richiesta e risposta)
- la _sintassi_ dei vari tipi di messaggi ovvero i campi del messaggio
- la _semantica_ dei campi ovvero come interpretare ed utilizzare I campi del messaggio
- le _regole_ per determinare quado e come un processo invia messaggi o risponde ai messaggi

## Architetture possibile per applicazioni di rete
le applicazioni di rete possono essere distribuite in più maniere a seconda delle responsabilità che ha ogni host come offrire servizi e chiedere 
#### Client-Server
- _Client_: l host che ha poche se non nessuno responsabilità e richiede al server un servizi
	- inizia contattando il server
	- richiede un servizio
- _Server_: L host che ha la maggior parte se non tutte le responsabilità e offre servizi al client
	- Risponde alle richieste del client
	- Sempre attivo
![[photo_2023-01-02_18-32-27.jpg]]
#### Peer-to-Peer:
- peer che possono sia offrire servizzi che inviare richieste 
#### Misto


