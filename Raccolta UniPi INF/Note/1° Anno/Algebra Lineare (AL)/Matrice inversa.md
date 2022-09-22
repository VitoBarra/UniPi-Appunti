---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Matrice inversa
---

### Definizione
sia una matrice $A \in M(n)$ la sua inversa è $A^{-1}$  ovvero una matrice tale che

$$
AA^{-1}=A^{-1}A=I_n
$$

Osservazione: non tutte le matrice sono invertibili

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 12.png]]

Osservazione: se $A$ invertibile $\implies det(A) \not= 0$

### Proprietà:

- $(AB)^{-1} = A^{-1} B^{-1}$

### Algoritmo per ricavare la matrice inversa:

 Si prende la matrice $n × (2n)$

$$
C = (A|l_n)
$$

ottenuta affiancando $A$ e la matrice identità $l_n$. Trasformiamo quindi $C$ usando l’algoritmo di Gauss-Jordan. Se $rk(A) = n$, alla fine dell’algoritmo tutti i pivot stanno nelle prime $n$ colonne. In particolare abbiamo ottenuto una nuova matrice $n × (2n)$

$$
 C' = (I_n | A^{-1})
$$

### esempio:

$$
\begin{pmatrix}
2 & 1 &| &1&0 \\
1 & 1 &| &0&1
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 0 &| &1&-1 \\
1 & 1 &| &0&1
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 0 &| &1&-1 \\
0 & 1 &| &-1&2
\end{pmatrix}
$$
