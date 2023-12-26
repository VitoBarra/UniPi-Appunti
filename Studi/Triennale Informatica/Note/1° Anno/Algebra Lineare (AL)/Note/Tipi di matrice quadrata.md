---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Tipi di matrice quadrata
---


Ricordiamo che $M(m, n, \mathbb{K})$ è lo spazio vettoriale formato dalle matrici $m \times n$ a coefficienti in $\mathbb{K}$. Come nei paragrafi precedenti, possiamo definire dei [[Sottospazio Vettoriale| sottospazzi vettoriali]] di $M(m, n, K)$ imponendo opportune restrizioni.
Data una matrice $A$, indichiamo con $A_{ij}$ oppure $a_{ij}$ i suoi coefficienti. Introduciamo delle definizioni che ci accompagneranno in tutto il libro. Una matrice $n \times n$ è detta quadrata.

Una matrice $A$ quadrata $n \times n$ è:

- $D(n) :$ diagonale se $a_{ij} = 0 \ \forall i \not= j$;
- $T^s(n):$ triangolare superiore se
- $T^i (n):$  triangolare inferiore se $a_{ij} = 0\ \forall i < j$
- $S(n):$  simmetrica se $a_{ij} = a_{ji} \ \forall i, j$
- $A(n):$  antisimmetrica se $a_{ij} = −a_{ji}\ \forall i, j$

### Esempi:

in ordine matrici diagonale, triangolare superiore, triangolare inferiore, simmetrica e antisimmetrica:

$$
\begin{pmatrix}
2 & 0 \\
0 & -1
\end{pmatrix} \ \ \ \begin{pmatrix}
1 & 9 \\
0 & \sqrt{2}
\end{pmatrix}\ \ \
\begin{pmatrix}
-1 & 0 \\
7 & 2
\end{pmatrix}\ \ \
\begin{pmatrix}
-1 & 2 \\
2 & 4
\end{pmatrix} \ \ \
\begin{pmatrix}
0 & 1 \\
-1 & 0
\end{pmatrix} \ \ \
$$

Si faccia attenzione alle definizioni: la matrice

$$
\begin{pmatrix}
0 & 0 \\
0 & 1
\end{pmatrix} \ \ \
$$

è al tempo stesso diagonale, triangolare superiore, triangolare inferiore e simmetrica

>[!info]  Osservazione
> La matrice nulla 0 è di tutti e 5 i tipi: è _diagonale_, _triangolare superiore_, _triangolare inferiore_, _simmetrica_ e _antisimmetrica_.
