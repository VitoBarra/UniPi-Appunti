---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
  - AIF
---

# Algoritmi di ricerca informati
---
gli **Algoritmi di ricerca informati** sono un classe di [[Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza una stima del costo per fare la scelta “migliore” in caso massimizzazione di un risultato va verso il nodo che stima meglio l aumentare del punteggio se bisogno minimizzare una valore sceglierà il nodo con costo stimato minore.

l idea di avere una stima serve per fare Pruning dei rami non utili riducendo cosi di la [[Complessita]] in spazio e tempo


gli algoritmi si basano si basano sulla [[Ricerca Best-first|Ricerca Best-first]] ma si utilizza una **_funzione di valutazione_** $f$ del nodo $n$  che dipende da un **euristica** $h(n)$. Un **euristica** è definita sul problema specifico utilizzano le informazioni che si hanno su quel problema,
generalmente è stima della distanza (costo del path rimanente) tra lo stato $n$ è il goal e vale che  $h(n) \geq 0$  per un qualsiasi nodo non **goal** e $h(goal) = 0$ 


la **funzione di valutazione ideale** è definita come:
$$f^*(n)=g^*(n)+h^*(n)$$
dove 
- $g^*(n)$ costo del cammino minimo da radica a $n$
- $h^*(n)$ costo del cammino minimo da $n$ a goal
- $f^*(n)$ costo del cammino minimo da nodo radice a nodo goal, passando $n$

in casi non ideali abbiamo:
- $g(n) \geq g^*(n)$ 
- $h(n)$ è una stima di $h^*(n)$ 
	- quindi si può sia sovrastimare che sottostimare
	 


### Algoritmi
- [[Ricerca Greedy best-frist]]
- [[Ricerca A-Star]]
- [[Ricerca Beam]]
- [[Ricerca IDA-Star]]
- [[Ricerca Best-first ricorsive (RBFS)]]
- [[Ricerca SMA-Star]]
