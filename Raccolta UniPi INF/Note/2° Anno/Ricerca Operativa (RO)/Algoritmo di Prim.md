
---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Algoritmo
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo di Prim
---


### *Teorema*

L’algoritmo di Prim trova un albero di copertura di costo minimo in tempo polinomiale.

### dimostrazione

Segue dalla condizione di ottimalità basata sui tagli.

### *Algoritmo*

1. Scegli un nodo $i \in N$, poni $S = \{i\}$ e $T = \emptyset$
2. se $|T|= n-1$ allora stop
3. Trova un arco $(u,v)$ di costo minimo tra gli archi de taglio $(S,N \backslash S)$ inserisci $(u,v)$ in  $T$
4. inserisci in $S$ l’ estremo di $(u,v)$ che non appartiene ad $S$ e torna al passo $2$

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1.png]]


#### Osservazione
>- Ad ogni iterazione dell’ algorismo di Prim l‘ insieme  $T$ è un albero
