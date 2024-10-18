---
Course: "[[Informatica concetti generali]]"
tags:
  - Esperimenti
topic: nota
---


# Calcolo pseudo-diagonali passando per uno punto
---

### algoritmo
con una [[Matrici]] di qualsiasi tipo si può ciacolare una simile diagonale principale passando per una qualsiasi coppia $ij$ usando la formula

$$
Dp_{kh}=
\begin{Bmatrix}
M(n)  :\forall i=j
\begin{cases}
x_{i+(k-h)\ ,\ j} \ \ \ \ \ if(h>k)\\
x_{i\ , \ j+(h-k)}
\end{cases}
\end{Bmatrix}

$$

per generare tutte le pseudo diagonali principali

$$
Dp =
\begin{Bmatrix}
\forall i,j\in[1,n]  \land
\forall k \in [2-n,n-2]\
|\  i-j=k
\end{Bmatrix}
$$

per la pseudo diagonale secondaria la formula è (ANCORA DA DAVVERO CAPIRE)

$$
Ds_{kh}=
 \begin{Bmatrix}
  M(n)  :
\forall i=j-n
\begin{cases}
x_{??} \ \ \ \ \ if(k>h)\\
x_{??}
\end{cases}
\end{Bmatrix}
$$

per generare tutte le pseudo diagonali secondarie

$$
Ds =
\begin{Bmatrix}
\forall i,j \in[1,n]  \land \forall k\in[3,2n-1]\
|\  i+j=k
\end{Bmatrix}
$$
