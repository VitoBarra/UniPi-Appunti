---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area:
SubTopic:
---
# Cammino di costo minimo
---
Il [[Cammino di costo minimo|cammino di costo minimo]] in un [[Graph Theory|grafo]] pesato tra due vertici $s$ e $t$ è un cammino il cui costo totale è minimo tra tutti i cammini che collegano $s$ a $t$.

Se ogni arco $(i,j)$ ha costo $c_{ij}$, il costo di un cammino $P=(v_0,v_1,\dots,v_k)$ è $c(P)=\sum_{h=0}^{k-1} c_{v_hv_{h+1}}$.

Il [[Cammino di costo minimo|cammino di costo minimo]] non coincide necessariamente con il cammino di lunghezza minima: se gli archi hanno pesi diversi, il criterio di ottimalità dipende dalla somma dei costi e non dal numero di archi attraversati.

La distanza tra due vertici $s$ e $t$ in un [[Graph Theory|grafo]] pesato è definita come $$d(s,t)=\min\{c(P):P \text{ cammino da } s \text{ a } t\}$$quando tale minimo esiste.

Se tutti i costi sono non negativi, ogni sottocammino di un [[Cammino di costo minimo|cammino di costo minimo]] è ancora un cammino di costo minimo tra i suoi estremi; questa proprietà di ottimalità locale è alla base di molti algoritmi sui cammini minimi.

La presenza di cicli di costo negativo modifica il problema: se da $s$ a $t$ è raggiungibile un ciclo con costo totale negativo, allora il costo minimo può non essere ben definito, perché il costo del cammino può essere diminuito indefinitamente.

Il problema dei cammini di costo minimo può essere formulato in diverse varianti:
- da una sorgente $s$ a un singolo vertice $t$
- da una sorgente $s$ a tutti gli altri vertici
- tra tutte le coppie di vertici

Nel caso di pesi non negativi il problema si presta a risoluzione efficiente; in presenza di pesi negativi occorrono algoritmi capaci di rilevare eventuali cicli negativi.

Il [[Cammino di costo minimo|cammino di costo minimo]] è strettamente collegato alla nozione di distanza in un [[Graph Theory|grafo]] pesato e a molte applicazioni di instradamento, pianificazione e ottimizzazione su reti.
