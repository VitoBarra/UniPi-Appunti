---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Teorema compatibilità delle norme
---
Sia $\|\cdot\|_v$ una _norma vettoriale_ su $\mathbb{F}^n$ e sia $\|\cdot\|_m$ la _norma matriciale_ indotta vale
$$\forall A\in\mathbb{F}^n, \forall v \in \mathbb{F}, \ \ \|Av\|_v\leq\|A\|_m\|v\|_v$$
##### Dimostrazione
Se $v=0$ allora la relazione vale. asseriamo pertanto che $v \not = 0$ si ha 
$$\left\|A\frac{v}{\|v\|} \right\| \leq \|A\|= \smash{\displaystyle\max_{\{z \in \mathbb{F}^n:\|z\|=1\}}}\|Az\|$$
e quindi la tesi segue la proprietà 2 delle [[Norme Matriciali e Norme Vettoriali|norme]] vettoriali