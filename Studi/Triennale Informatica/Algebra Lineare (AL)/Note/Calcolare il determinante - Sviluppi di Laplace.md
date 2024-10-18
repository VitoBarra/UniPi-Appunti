---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
Area: 
topic: 
SubTopic: "[[Determinante di una matrice]]"
---
# Calcolare il determinante - Sviluppi di Laplace
---
gli __sviluppi di Laplace__ sono un tecnica per calcolare piu velocemente il [[Determinante di una matrice|determinante]]
Sia
- $A$  una [[Matrici|matrice]] $n \times n$ con $n ≥ 2$. 
- $C_{ij}$ la sottomatrice $(n−1)\times(n−1)$ ottenuta da $A$ rimuovendo la $i$-esima riga e la $j$-esima colonna.
allora lo __sviluppo di laplace__ permette di calcolare il determinante come:$$
det(A) = \sum_{j=1}^{n}(-1)^{i+j}a_{ij}\ det(C_{ij})

$$



![[Studi/Triennale Informatica/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 18.png]]


$$
\begin{array}{}

det\begin{pmatrix}
1 & -1 & 0 \\
2 & -1 & 5 \\
1 & 1 & -1
\end{pmatrix} & = \\

1 \cdot
det\begin{pmatrix}
-1 &5 \\
1 & -1
\end{pmatrix}
-(-1)
det\begin{pmatrix}
2 &5 \\
1 & -1
\end{pmatrix}
+0 \cdot
det\begin{pmatrix}
2 &-1 \\
1 & 1
\end{pmatrix}  & = \\
 -4-7+0=-11
\end{array}
$$

