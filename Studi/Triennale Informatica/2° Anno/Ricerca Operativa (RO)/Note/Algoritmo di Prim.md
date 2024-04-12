---
Subject: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
Area: 
topic: 
SubTopic:
---

# Algoritmo di Prim
---

### Teorema

L’[[Algoritmi|algoritmo]] di Prim trova un [[Albero di copertura|albero di copertura]] di costo minimo in [[Complessita|complessità]] in tempo polinomiale.

### dimostrazione

Segue dalla [[Condizione di ottimalità sui tagli|condizione di ottimalità basata sui tagli]].

### Algoritmo

1. Scegli un nodo $i \in N$, poni $S = \{i\}$ e $T = \emptyset$
2. se $|T|= n-1$ allora stop
3. Trova un arco $(u,v)$ di costo minimo tra gli archi de taglio $(S,N \backslash S)$ inserisci $(u,v)$ in  $T$
4. inserisci in $S$ l’ estremo di $(u,v)$ che non appartiene ad $S$ e torna al passo $2$

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1.png]]
una proprieta di questo algoritmo e che ad ogni iterazione dell’ algorismo di Prim l‘ insieme  $T$ è un [[Struttura dati - Albero|albero]]

