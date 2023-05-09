---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Algoritmi di ricerca informati per AI
---
è un  classe di  [[Algoritmi di ricerca per AI|Algoritmo di ricerca]] che utilizza una stima del costo per fare la scelta “migliore” in caso massimizzazione di un risultato va verso il nodo che stima meglio l aumentare del punteggio se bisogno minimizzare una valore sceglierà il nodo con costo stimato minore.

l idea di avere una stima serve per fare Pruning dei rami non utili riducendo cosi di la [[Complessita]] in spazio e tempo


gli algoritmi si basano su [[Ricerca di costo uniforme UC-AI|UC]] ma si utilizza una _funzione  di valutazione_ del nodo $n$ al posto del costo del percorso $g$. questa è definita come: 
$$f(n)= g(n)+h(n)$$
dove 
- $g(n)$ è il costo del cammino dal nodo di partenza al nodo $n$
- $h(n)$ è il la funzione di valutazione euristica
	- definita sul problema specifico utilizzano le informazioni che si sanno su quel problema
	- definita come stima di distanza dal nodo $n$ al nodo $goal$ 
- $h(n) \geq 0$
- $h(goal) = 0$ 

la scelta di $f$ modifica la strategia di ricerca infatti si puo scegliere una $f$ in modo che questa ricerca si comporti come [[Ricerca in profondita DF-AI|DL]] 

### Algoritmi
[[Ricerca Greedy best-frist AI]]
[[Ricerca A-Star per AI]]
[[Ricerca Beam per AI]]
[[Ricerca IDA-Star per AI]]
[[Ricerca Best-first ricorsive (RBFS) per AI ]]
[[Ricerca SMA-Star per AI]]
