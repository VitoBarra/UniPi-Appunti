---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - IA
Area: 
topic: "[[Algoritmi di ricerca informati]]"
SubTopic:
---

# Proprietà delle euristiche per ricerca informata
---


## Ammissibilità di un euristica
un **euristica ammissibile** è una sottostima di $h^*$	 $$\forall n.h(n) \leq h^*(n)$$
per essere anche una buona euristica il nodo goal deve avere distanza 0



#### Consistenza di un euristica
Un euristica consistente è un euristica per cui valgono le seguenti proprietà
- $\forall n.h(n) \leq c(n,a,n’) + h(n’)$
	- Dove $n’$ è un successore di $n$
	- $c(n,a,n’)$ è il costo per passare dal nodo $n$ al nodo $n’$ tramite l azione $a$
	- questa formula viene direttamente dal [[Diseguaglianza triangolare|diseguaglianza triangolare]]
-  da cui possiamo dire $f(n) \leq f(n’)$ 
	- $f$ non decresce mai da qui il termine [[Funzione Monotona|Monotona]]
	![[IMG - Euristica consistente per A-Star.png]]
