---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Matrice Trasposta
---
### Definizione
la matrice trasposta di una matrice $A$  è indicata come $^tA$  ed è definita scambiando righe e colonne

$$
({}^t\!A)_{ij} =A_{ji}
$$

### esempi:

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

- $A\in M(n) \implies {}^t\!A\in M(n)$[[]]
- $A \in S(n) \iff {}^t\!A=A$[[]]
- $A \in A(n) \iff {}^t\!A=-A$[[]]