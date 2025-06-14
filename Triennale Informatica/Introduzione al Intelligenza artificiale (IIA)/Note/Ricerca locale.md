---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
---

# Algoritmi di Ricerca locale
---
Gli **Algoritmi di Ricerca locale** sono una classe di [[Algoritmi|algoritmi]] per risolvere **[[Problemi di ricerca|problemi di ricerca]]** che sono caratterizzati dal fatto di spostarsi da uno stato iniziale nei suoi immediati vicini senza valutare i passi successivi e senza ricordando il percorso fatto fino allo stato correte. Infatti si utilizza quando solo lo stato $goal$ è importante e quindi quando non interessa avere il **path** per arrivare a quel $goal$, anche perche a volte risalire al path avendo la soluzione è triviale.

le assunzioni sul [[Definizione di Problemi-Ambienti|Ambiente]] sono: 
  _Statico_ | _Parzialmente Osservabile_ | _Continuo_/discreto | _Non Deterministico_ | _Sconosciuto_
            

Quesiti algoritmi sono solitamente implementati come [[problemi di ottimizzazione|problemi di ottimizzazione]] dove si vuole massimizzare una data funzione obiettivo, si puo immaginare una superfice della funzione obiettivo come:
![[IMG - Ricerca locale land scape della funzione obiettivi 1D.png]]
il landscape di una funzione obiettivo puo avere alcune feature quali 
- **massimo globale**: il valore piu alto per tutta la funziones
- **massimo locale**: un valore per cui tutti i suoi vicini hanno valore piu basso ma questo non è il massimo globale
- **Plateaus**: un zona piatta, ovvero un massimo locare dove pero alcuni vicini hanno lo stesso valore de massimo. 
- **Shoulder**: un **Plateaus** che porta ad un  altra zona di risalita


### Algoritmi
- [[Ricerca Hill Climbing]]
- [[Ricerca Simulated Annealing]]
- [[Ricerca Local beam]]
- [[Ricerca Generativa-Evolutiva]]