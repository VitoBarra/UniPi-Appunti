---
Course: Algebra Lineare
topic: nota
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Calcolare autovalori e autovettori
---
Per calcolare i [[Calcolare autovalori e autovettori|autovettori]] di una [[Matrici]] dobbiamo prima calcolare il _[[Polinomi|polinomio]] caratteristico definito_ come

$$
P_A(\lambda)=det(A-\lambda I_n)=det
\begin{pmatrix}
a_{11}-\lambda &a_{12} &\cdots &a_{1n} \\

a_{21} &a_{22}-\lambda &\cdots &a_{2n} \\

\vdots &\vdots &\ddots &\vdots \\

a_{n1} &a_{n2} &\cdots &a_{nn}-\lambda \\
\end{pmatrix}
$$

il polinomio ha forma

$$
P_A(\lambda)=a_n\lambda^n+a_{n-1}\lambda^{n-1}+\dots+a_0
$$

è alcuni sui coefficienti sono noti

- $a_n = (-1)^n$
- $a_{n−1} = (−1)^{n−1}tr(A)$
- $a_0 =det(A)$

una volta trovato il polinomio caratteristico per trovare gli autovalori basta cercare le radici del polinomio

per trovare l'autovettore associato basta risolvere l’equazione

$$
Av=\lambda_iv
$$

oppure

$$
(A-\lambda I)v=0
$$
