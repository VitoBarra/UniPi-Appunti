---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - AIF
  - IA
Area: 
topic: 
SubTopic:
---

# Proprieta delle euristiche
---
Alcune proprietà delle euristiche negli [[algoritmi di ricerca informata|algoritmi di ricerca informata]]  

indicando con  $^*$ qualsiasi cosa considerata ottima 
#### Ammissibilità di un euristica
un **euristica ammissibile** è una **sottostima** di $h^*$	quindi vale che $$\forall n.h(n) \leq h^*(n)$$
#### Consistenza di un euristica
Un __euristica consistente__ è un euristica per vale la seguente proprietà
**sia**:
- Dove $n’$ è un successore di $n$
- $c(n,a,n’)$ è il costo per passare dal nodo $n$ al nodo $n’$ tramite l'azione $a$
**allora** vale che: $$\forall n.h(n) \leq c(n,a,n’) + h(n’)$$questa formula viene direttamente dal [[Diseguaglianza triangolare|diseguaglianza triangolare]]
se vale che $c_{ij}\ge\epsilon>0$ allora da questa proprietà possiamo dire che $f(n) \leq f(n’)$ ovvero $f$ **cresce ad ogni step** e per questo è una funzione [[Funzioni|Monotona]] ![[IMG - Euristica consistente per A-Star.png]]

