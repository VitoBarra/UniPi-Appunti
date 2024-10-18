---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Testing
---
il testing è una applicazione dei  [[Concetti di verifica e validazione]]

Una prova formale di correttezza corrisponderebbe al esecuzione del sistema con tutti i _possibili input_ questo è definito come test esaustivo. questo risicherebbe tempo infinito con insieme infiniti e anche limitando l insieme se questo è molto grande ci vorrebbe troppo tempo per essere fattibile 


>[!warning] Tesi di Dijkstra
il test di un programma può rilevare la presenza di difetti ma non dimostrare l assenza 


## Tecniche di verifica: Verifica Statica
- Verifica che non prevede l esecuzione del programma
- Metodi manuali 
	- [[Tecniche di lettura del codice Strutturata|Basati sulla lettura del codice]] (desk-check)
		- più pratica e intuitiva 
		- Ideale per alcune caratteristiche di qualità
		- convenienza economica 
			- costi dipendere dalle dimensione del codice 
			- bassi costi di infrastruttura
			- buona prevedibilità dei resultati
	- più comunemente usati ma  meno formale documentati 
- Metodi formati o analisi statica supportata dal strumenti 
	- Tecnica basata sulla dimostrazione formale di correttezza di un modello finito _(dimostrazione possibile)_ e instanziazione del modello.
	- Model checking 
		![[FD85CAAE-BB04-4955-BC57-BE6BB85671F6.jpeg]]
	- Esecuzione simbolica
	- Interpretazione astratta
	- Theorem proving 
	
## Tecniche di verifica: Verifica dinamica
1. Progettazione 
	- input 
	- output atteso 
	- ambiente di esecuzione del test 
2. esecuzione del codice
3. analisi del risultati
	- output ottenuto con l esecuzione vs output atteso
4. debugging



 [[Tecniche di progettazione casi di test]]


[[Problema del oracolo]]
 


