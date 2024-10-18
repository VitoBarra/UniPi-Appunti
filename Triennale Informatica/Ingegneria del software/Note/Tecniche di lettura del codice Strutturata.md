---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Tecniche di lettura del codice Strutturata
---
## inspection
- Si esegue una lettura mirata dal codice(guidata da un lista di controllo)
- #### Obbiettivi 
	- rivelare la presenza di difetti
- Strategia 
	- Focalizzare la ricerca su aspetti ben definiti(error guessing)
- Agenti
	- verificatori diversi del programmatore 

### Fasi 
1.  Pianificazione 
2. definizione della lista di controllo
	- Sono frutto del espressione degli ispettori 
	- Contengono tipicamente aspetti che non possono essere controllati in maniere automatica 
	- le liste di controllo sono aggiornate ad ogni iterazione di inspection
3. lettura del codice
4. correzione dei difetti


## Walkthrough
1. Obiettivo 
	- rivelare la presenza di difetti 
	- eseguire una lettura critica del codice
2. Strategia
	- percorrere il codice simulandone l esecuzione 
3. Agenti
	- gruppi misti ispettori e sviluppatori 

### Fasi
1. Pianificazione
2. lettura del codice
3. correzione dei defetti

#### Vantaggi 
- Pratica e intuitività 
- ideale per alcune caratteristiche di qualità 
- Convenzione economica
	- costi i prendentesi dalle dimensioni del codice 
	- bassi costi di infrastruttura 
	- buona prevedibilità devo risultati 

#### Confronto tra tecniche 

1. _Affinità_  
	- Controlli stati basati su desk-test
	- Programmatori e verificatori contrapposti 
1. _Differenze_
	- inspection basato su errori presupposti 
	- Inspection più rapido 
	- Walkthrough e più completo 

