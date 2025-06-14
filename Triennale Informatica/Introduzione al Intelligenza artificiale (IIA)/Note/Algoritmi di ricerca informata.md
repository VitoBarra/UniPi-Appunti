---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Algoritmi di ricerca informata
---
gli **Algoritmi di ricerca informati** sono un classe di [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] che utilizza una stima del costo per fare la scelta “migliore”
- in caso **massimizzazione** sceglie il nodo che stima meglio l'aumentare del punteggio
- in caso di minizazione sceglie il nodo con costo stimato minore
l'idea di avere una stima serve per fare Pruning dei rami non utili riducendo cosi di la [[Complessita]] in spazio e tempo

gli algoritmi si basano si basano sulla [[Ricerca Best-first|Ricerca Best-first]] ma si utilizza una **_funzione di valutazione_** $f$ del nodo $n$  che dipende da una funzione **euristica** che appunto fornisce una stima della distanza del nodo $n$ al nodo goal. la **funzione euristica** è definita sul problema specifico utilizzano le informazioni che si hanno su quel problema.

### Algoritmi
- [[Ricerca Greedy best-frist]]
- [[Ricerca A-Star]]
- [[Ricerca Beam]]
- [[Ricerca IDA-Star]]
- [[Ricerca Best-first ricorsive (RBFS)]]
- [[Ricerca SMA-Star]]
