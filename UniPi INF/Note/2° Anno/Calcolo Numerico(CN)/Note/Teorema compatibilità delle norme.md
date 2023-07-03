---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Teorema compatibilità delle norme
---
Sia $\|\cdot\|_v$ una _[[Norme Matriciali e Norme Vettoriali|norma vettoriale]]_ su $\mathbb{F}^n$ e sia $\|\cdot\|_m$ la _[[Norme Matriciali e Norme Vettoriali#Teorema norme matriciali indotte da norme vettoriali|norma matriciale indotta]]_ vale
$$\forall A\in\mathbb{F}^{n\times n}, \forall v \in \mathbb{F}^{n}, \ \ \|Av\|_v\leq\|A\|_m\|v\|_v$$
##### Dimostrazione
per il caso $v=0$ la relazione è sempre vera
per il caso $v \not = 0$ si ha 
$$\left\|A\frac{v}{\|v\|} \right\| \leq \|A\|= \smash{\displaystyle\max_{\{z \in \mathbb{F}^n:\|z\|=1\}}}\|Az\|= \|z\|\|A\|$$
e quindi la tesi segue dalla proprietà 2 (la linearità) delle [[Norme Matriciali e Norme Vettoriali|norme]] vettoriali