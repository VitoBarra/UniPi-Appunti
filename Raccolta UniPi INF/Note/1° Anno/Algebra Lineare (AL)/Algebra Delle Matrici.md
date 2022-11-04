---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Algebra Delle Matrici
---

### Prodotto riga per colonna

 Se $A$ è una [[matrice]] $m\times n$ e $B$ è una matrice $n \times p$  il prodotto $AB$ è una nuova matrice $m \times p$ definita nel modo seguente: l’elemento $(AB)_{ij}$ della nuova matrice $AB$ è

$$
(AB)_{ij} =
\sum_{k=1}^n A_{ik}B_{kj} =
A_{i1}B_{1j}+\cdots+A_{in}B_{nj}
$$

Questo tipo di prodotto fra matrici si chiama prodotto riga per colonna perché l’elemento $(AB)_{ij}$ si ottiene facendo un opportuno prodotto fra la riga $i\text{-esima } A_i$ di $A$ e la colonna $j\text{-esima } B^j$ di $B$

un esempio:

$$
\begin{pmatrix}
1 &  2 \\
-1 & 1 \\
0 & 3
\end{pmatrix}
\cdot
\begin{pmatrix}
-1 & 2 & 0 & 1 \\
3 & 0 & 3 & 0
\end{pmatrix}
=
\begin{pmatrix}
 5 & 2 & 6 & 1 \\
4 & -2 & 3 & -1 \\
9 & 0 & 9 & 0
\end{pmatrix}
$$


![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 13.png]]

### proprietà algebriche matrici:

- $A =  M^{-1}BM,C=M^{-1}DM \implies AC=M^{-1}BDM$
- $A=M^{-1}BM \implies A^k = M^{-1}B^{k}M$
