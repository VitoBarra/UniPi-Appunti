---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Algoritmi di ricerca informati
---
è un  classe di  [[AI - Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza una stima del costo per fare la scelta “migliore” in caso massimizzazione di un risultato va verso il nodo che stima meglio l aumentare del punteggio se bisogno minimizzare una valore sceglierà il nodo con costo stimato minore.

l idea di avere una stima serve per fare Pruning dei rami non utili riducendo cosi di la [[Complessita]] in spazio e tempo


gli algoritmi si basano su [[AI - Ricerca di costo uniforme UC|UC]] ma si utilizza una _funzione  di valutazione_ del nodo $n$ al posto del costo del percorso $g$. questa è definita come: 
$$f(n)= g(n)+h(n)$$
dove 
- $g(n)$ è il costo del cammino dal nodo di partenza al nodo $n$
- $h(n)$ è il la funzione di valutazione euristica
	- definita sul problema specifico utilizzano le informazioni che si sanno su quel problema
	- definita come stima di distanza dal nodo $n$ al nodo $goal$ 
- $h(n) \geq 0$
- $h(goal) = 0$ 

la scelta di $f$ modifica la strategia di ricerca infatti si puo scegliere una $f$ in modo che questa ricerca si comporti come [[AI - Ricerca in profondita|DL]] 

### Algoritmi
- [[AI - Ricerca Greedy best-frist]]
- [[AI - Ricerca A-Star]]
- [[AI - Ricerca Beam]]
- [[AI - Ricerca IDA-Star]]
- [[AI - Ricerca Best-first ricorsive (RBFS)]]
- [[AI - Ricerca SMA-Star]]
