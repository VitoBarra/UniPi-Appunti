---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Distanza geodetica
---
La **distanza geodetica** è un tipo di [[Definizione di distanza|distanza]] definita su una [[Superfici|superficie]] o più in generale su una [[Manifolds (Varieta)|varietà differenziabile]] e rappresenta la lunghezza del percorso più breve che collega due punti seguendo la superficie stessa.

__Siano__ $p, q$ due punti su una superficie curva (es. una [[Sfera|sfera]])  
__Allora__ si definisce distanza geodetica il numero  
$$d_{\text{geo}}(p, q) = \inf_{\gamma} \int_a^b \|\gamma'(t)\|\, dt$$  
dove $\gamma: [a,b] \rightarrow M$ è una [[Curva regolare|curva regolare]] che collega $p$ a $q$ all'interno della superficie $M$.

La distanza geodetica misura quindi la lunghezza della **minima geodetica** tra due punti, ovvero il cammino più breve "ammesso" dalla geometria della superficie.  
Nel caso di superfici curve come la [[Sfera|sfera]], la geodetica corrisponde a un [[Arco di circonferenza massima|arco di cerchio massimo]].

Rispetto alla [[Distanza euclidea|distanza euclidea]], che ignora la curvatura dello spazio, la distanza geodetica tiene conto della forma del dominio in cui si trovano i punti. 
solitamente vale che la **distanza geodetica** si sempre maggiore di quella [[Distanza euclidea|euclidea]] $$d_{geo}\geq d_{euc}$$
