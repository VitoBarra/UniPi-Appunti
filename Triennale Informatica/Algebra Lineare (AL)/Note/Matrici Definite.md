---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
Area:
topic:
SubTopic:
---
# Matrici Definite
---
Le **matrici definite** sono [[Matrici quadrate|matrici quadrate]] classificate in base al segno della forma quadratica associata. Nel caso reale si considera tipicamente una [[Matrici quadrate|matrice quadrata]] simmetrica $M$ e la quantita $x^{\top}Mx$ per ogni vettore non nullo $x$.

Una matrice reale simmetrica $M$ e:
- **definita positiva** se $$x^{\top}Mx>0 \qquad \forall x\neq 0$$
- **semidefinita positiva** se $$x^{\top}Mx\geq 0 \qquad \forall x\neq 0$$
- **definita negativa** se $$x^{\top}Mx<0 \qquad \forall x\neq 0$$
- **semidefinita negativa** se $$x^{\top}Mx\leq 0 \qquad \forall x\neq 0$$
- **indefinita** se la forma quadratica $x^{\top}Mx$ assume sia valori positivi sia valori negativi

L'intuizione e che una matrice definita controlla il segno della forma quadratica associata. La quantita $x^{\top}Mx$ assegna a ogni vettore un numero reale, e la classificazione della matrice descrive proprio come questo numero puo variare: una matrice definita positiva lo rende sempre positivo per ogni vettore non nullo, una semidefinita positiva non lo rende mai negativo, mentre una matrice indefinita puo produrre valori di segno diverso. In questo senso una matrice definita positiva si comporta come una misura quadratica sempre coerente, mentre una matrice indefinita descrive una geometria in cui direzioni diverse producono comportamenti opposti.

Nel caso complesso la definizione analoga si formula per matrici **ermitiane**, sostituendo il trasposto con il trasposto coniugato:
$$
z^{*}Mz
$$
con $z\neq 0$.

In particolare, una matrice ermitiana $M$ e definita positiva se
$$
z^{*}Mz>0 \qquad \forall z\neq 0
$$

La simmetria, o nel caso complesso l'ermiticita, e essenziale nel contesto standard della definizione, perche garantisce che la forma quadratica assuma valori reali.
