---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Agenti risolutori di problemi
---
## Agenti risolutori di problemi
- Adottano il paradigma della _risoluzione di problemi_ come ricerca in uno spazio di stati (problem solving). 
-  Sono [[AI - Agenti Razionali#Agenti basati su modello|agenti con modello]] (storia percezioni e stati) che adottano una rappresentazione atomica dello stato 
-  Sono particolari [[AI - Agenti Razionali#Agenti con obiettivo|agenti con obiettivo]], che _pianificano_ l’intera sequenza di mosse prima di agire


## Passi da eseguire per l utilizzo
1. Determinazione obiettivo (un insieme di stati in cui l obbiettivo è soddisfatto)
2. [[#Formulazione del problema]]
	1. Design di questo per ora _non_ automatico
	2. rappresentazione degli _stati_
	3. rappresentazioni delle _azioni_
3. Determinazione della soluzione mediante [[AI - Algoritmi di ricerca|Ricerca]] (esecuzione di un piano un algoritmo)
4. Esecuzione del piano


## Formulazione del problema
1. Definizione degli stati $s$
2. Stato iniziale
3. Azioni possibili in $Azioni(s)$
4. Modello di transizione:
	1. Risultato: $Stato \times Azione \rightarrow Stato$
	2. queste definiscono lo _spazio degli stati_ implicitamente. fare altrimenti con una definizione esplicita può essere molto oneroso in termini di spazio
5. Test Obiettivo
	- un insieme di stati obiettivo
	- Goal-Test : $Stato \rightarrow \{true,false\}$
6. Costo del cammino
	- somma dei costi delle azioni (costo dei passi)
7. costo di passo: $c(s,a,s')$
	- il costo di un azioni passo non è mai negativo