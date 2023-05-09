---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Autovettori e Autovalori
---
sua di uno [[Spazio Vettoriale|spazio vettoriale]] $V$ su $\mathbb{K}$ e $T:V \rightarrow V$ un [[Isomorfismo e Endomorfismo|endomorfismo]] , chiamiamo _autovettore_ un vettore $v \in V,v \not= 0$  e un _autovalore_ di $T$ associato a $v$  un qualunque $\lambda \in \mathbb{K}$ tale che

$$
T(v)=\lambda v
$$

### Osservazioni:
- tutti i vettori dello $Span(v)$ sono _autovettori_ con lo stesso _autovalore_
- Gli _autovettori_ $v$ con _autovalore_ $\lambda =0$ sono i vettori $v \not =0 \land v \in ker(T)$
- Gli _autovettori_ $v$ con _autovalore_ $\lambda =1$ sono i vettori $v \not =0$  che sono [[Punti Fissi]]


![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 7.png]]

![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 4.png]]

### Esistenza di autovettori:
- se $dim(\R^n)$ é dispari esiste sempre almeno un autovettore in $\R$ questo perché se $P_A(\lambda)$  ha grado dispari ha sempre una radice in $\R$
- Esiste sempre un autovalore nel campo $\mathbb{C}$ questo perché il [[Calcolare autovalori e autovettori|polinomio caratteristico]] $P_A(\lambda)$ ha sempre una radice in $\mathbb{C}$
