---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---


# Metodi locali per SAT
---
è una classe di algoritmi di tipo [[Ricerca locale|locale]] per la risoluzione di [[Problema della Soddisfacibilita (SAT)|SAT]] nel contesto del utilizzo di [[Agenti Logici - Calcolo proposizionale|Agenti con calcolo proposizionale]]. dove:
-  Gli stati Sono interpretazioni complete
	- A _tutti_ i simboli preposizionali è assegnato un valore
- l _obiettivo_ è un assegnamento che soddisfa tutte le clausole, ovvero un _modello_
- si parte da un assegnamento causuale
- ad ogni passo si cambia il valore di un simbolo proposizionale , si fa un _flip_
- gli stati sono valutati contando il numero di clausole _soddisfatte_
	- vogliamo massimizzare il numero di clausole soddisfatte.




### Walk-Sat
- Sceglie a caso una clausola non ancora soddisfatta
- individua un simbolo da modificare, scegliendo con probabilità $p$
	- scegliere un simbolo a caso (_passo casuale_, random walk)
	- Scegliere quello che rende piu clausole soddisfatte (_passo di ottimizzazione_)
- Dopo un certo numero di _flip_ si arrende

#### Analisi 
-  se _NON_ esiste una modello e max-flip $= \infty$ l algoritmo non termina 
	- non puo essere usato per verificare l insoddisfacibilita
- Ma se vogliamo un algoritmo che termina questo è necessariamente incompleto




