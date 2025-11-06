---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - AIF
  - IIA
Area: 
topic: 
SubTopic:
---

# Ricerca informata - Proprieta delle euristiche 
---
Alcune proprietà delle euristiche usate negli [[algoritmi di ricerca informata|algoritmi di ricerca informata]].


un **euristica ammissibile** è una **sottostima** del costo ottimo $h^*$quindi vale che $$\forall n.h(n) \leq h^*(n)$$



Un __euristica consistente__ è un euristica per cui vale la seguente proprietà
**sia**:
- Dove $n’$ è un successore di $n$
- $c(n,a,n’)$ è il costo per passare dal nodo $n$ al nodo $n’$ tramite l'azione $a$
**allora** vale che: $$\forall n.h(n) \leq c(n,a,n’) + h(n’)$$questa formula viene direttamente dal [[Diseguaglianza triangolare|diseguaglianza triangolare]]
se vale che $c_{ij}\ge\epsilon>0$ allora da questa proprietà possiamo dire che $f(n) \leq f(n’)$ ovvero $f$ **cresce ad ogni step** e per questo è una funzione [[Funzioni|Monotona]] ![[IMG - Euristica consistente per A-Star.png]]

