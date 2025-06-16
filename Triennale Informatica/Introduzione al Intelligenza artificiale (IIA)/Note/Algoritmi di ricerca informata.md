---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
  - AIF
---

# Algoritmi di ricerca informata
---
gli **Algoritmi di ricerca informati** sono un classe di [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] che utilizza una stima del costo per fare la scelta “migliore” in caso massimizzazione di un risultato va verso il nodo che stima meglio l aumentare del punteggio se bisogno minimizzare una valore sceglierà il nodo con costo stimato minore.

l idea di avere una stima serve per fare Pruning dei rami non utili riducendo cosi di la [[Complessita]] in spazio e tempo


gli algoritmi si basano si basano sulla [[Ricerca Best-first|Ricerca Best-first]] ma si utilizza una **_funzione di valutazione_** $f$ del nodo $n$  che dipende da un **euristica**. Un **euristica** è definita sul problema specifico utilizzano le informazioni che si hanno su quel problema.





### Algoritmi
- [[Ricerca Greedy best-frist]]
- [[Ricerca A-Star]]
- [[Ricerca Beam]]
- [[Ricerca IDA-Star]]
- [[Ricerca Best-first ricorsive (RBFS)]]
- [[Ricerca SMA-Star]]
