---
Course: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---


# Matrice Trasposta
---
sia $A$ una [[Matrice]] 
_allora_ la trasposta di $A$ e' indicata come $A^T$  e' una matrice tale che$$
a^T_{ij} =a_{ji}
$$ovvero si scambiano righe e colonne

### esempi

$$
A=
\begin{pmatrix}
a_{11} &a_{12} \\
a_{21} &a_{22} \\
a_{31} &a_{32}
\end{pmatrix}
\ \ \
{}^t\!A=
\begin{pmatrix}
a_{11} &a_{21} & a_{31}\\
a_{12} &a_{22} & a_{32}\\
\end{pmatrix}
$$

### valgono le proprietà:

- ${}^t(A+B)={}^t\!A+{}^t\!B$
- ${}^t(\lambda A)=\lambda\ {}^t\!A$

### relazioni con gli spazi delle matrici:

- $A\in M(n) \implies {}^t\!A\in M(n)$
- $A \in S(n) \iff {}^t\!A=A$
- $A \in A(n) \iff {}^t\!A=-A$