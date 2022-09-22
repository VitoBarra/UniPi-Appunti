---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Determinante di una matrice
---

### Definizione

Sia $A$ una matrice quadrata $n \times n$. Il determinante di $A$ è il numero

$$
det(A) = \sum_{\sigma \in S_{n}} sng(\sigma)
a_{1\sigma(1)}
\cdots
a_{n\sigma(n)}
$$

dove:

- $S_n$ = l insieme di $n!$ permutazioni
- $sgn(\sigma) = \pm1$ che indica il segno della permutazioni
- $\sigma(i) =$ una $i$-esima permutazione
- $a_{ij} =$  il $ij$-esimo elemento della matrice

### casi semplici:

se la matrice $A \in M(n)$ è [triangolare (superiore o inferiore) o diagonale](obsidian://open?vault=UniPi-Appunti&file=Raccolta%20UniPi%20INF%2FNote%2F1%C2%B0%20Anno%2FAlgebra%20Lineare%20(AL)%2FTipi%20di%20matrice%20quadrata)

$$
A=
\begin{bmatrix}
a_{11} & a_{12} & \cdots &a_{1n}\\
0 & a_{22} & \cdots &a_{2n}\\
\vdots & \vdots & \ddots &\vdots\\
0 & 0 & \cdots &a_{nn}\\
\end{bmatrix}
\ \ \ \ \ \ \
A=
\begin{bmatrix}
a_{11} & 0 & \cdots & 0\\
a_{21} & a_{22} & \cdots & 0\\
\vdots & \vdots & \ddots &\vdots\\
a_{m1} & a_{m2} & \cdots &a_{nn}\\
\end{bmatrix}\\
A=
\begin{bmatrix}
a_{11} & 0 & \cdots & 0\\
0 & a_{22} & \cdots & 0\\
\vdots & \vdots & \ddots &\vdots\\
0 & 0 & \cdots &a_{nn}\\
\end{bmatrix}
$$

allora il determinante diventa:

$$
det(A)=a_{11}a_{22}\cdots a_{nn}
$$

---

# calcolare il determinante più agilmente

## sviluppi di Laplace

Sia $A$  una matrice $n \times n$ con $n ≥ 2$. Indichiamo con $C_{ij}$ la sottomatrice
$(n−1)\times(n−1)$ ottenuta da $A$ rimuovendo la $i$-esima riga e la $j$-esima colonna.

$$
det(A) = \sum_{j=1}^{n}(-1)^{i+j}a_{ij}\ det(C_{ij})

$$



[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 18.png]]

esempi:

$$
det\begin{pmatrix}
1 & -1 & 0 \\
2 & -1 & 5 \\
1 & 1 & -1
\end{pmatrix}=
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
\end{pmatrix}= -4-7+0=-11

$$

---

## Mosse di Gauss

Sia una matrice $A \in M(n)$  applicando le mosse di Gauss il determinante cambia nei seguenti modi

- Se $A'$ è ottenuta da $A$ scambiando due righe, $det(A') = − det(A)$
- Se $A'$ è ottenuta da $A$ moltiplicando una riga di $A$ per uno scalare $\lambda$, allora                $det(A') = \lambda det(A)$
- Se $A'$  è ottenuta da $A$ aggiungendo ad una riga il multiplo di un’altra riga, allora       $det(A') = det(A)$

---

Sia una matrice $A \in M(n)$ e supponiamo che la $i$esima colonna sia esprimibile come combinazione lineare di vettori colonna del tipo

$$
A^i = λ_1v_1 + · · · + λ_hv_h
$$

per qualche $v_j \in K^n$ e $λ_j ∈ K$. Sia $B_j$ la matrice ottenuta da $A$ sostituendo la colonna $A^i$
con $v_j$  per $j = 1,\dots,h$ vale



$$
det(A)=\lambda_1 det(B_1)+\cdots+\lambda_h det(B_h)
$$

Corrolario: siccome $det(A) =det({}^t\!A)$ questo vale anche per le righe

Esempi:

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 1 11.png]]

