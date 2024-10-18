---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic: "[[Metodi Iterativi per soluzioni di sistemi lineari]]"
---
# Metodo di  gauss-seidel (metodo di spostamento simultanei)
---
è un [[Metodi Iterativi per soluzioni di sistemi lineari|metodo iterativo]] basato su decomposizione di $A$ per il calcolo di una [[Soluzioni di un sistema lineare|soluzione di un sistema lineare]].
fattorizziamo $A = M - N$ con
- $M=D-L$ (la parte triangolare inferiore della matrice $A$)
- $N = U$
- la _matrice di iterazione_ $G=(D-L)^{-1}U$ 
dove  $$A =
\begin{bmatrix}
 &  &  &  &  & \\
 &  &  &  -U&  & \\ 
 &  & D &  &  & \\ 
 &  -L&  &  &  & \\
 &  &  &  &  & \\
\end{bmatrix}$$
![[Pasted image 20230510215538.png]]
>[!warning]
>posso applicare questo metodo solo alle matrici con $a_{ii} \not= 0\ \ \ \forall i =1,\dots,n$ ovvero solo a quelle matrici che _NON_ hanno elementi nulli sulla _diagonale_. cosi non fosse $D-L$ non sarebbe [[Matrice inversa|invertibile]].

quindi il _metodo_ è quindi
$$\begin{cases}
x^{(0)} \in \mathbb{K}^n\\
x^{(k+1)} = Gx^{(k)}+(D-L)^{-1}b
\end{cases}$$
possiamo Riscrivere la seconda equazione come 
$$
\begin{array}{}
x^{(k+1)} &=& Gx^{(k)}+(D-L)^{-1}b \\
x^{(k+1)} &= &(D-L)^{-1}(Ux^{(k)}+b)  \\
(D-L)x^{(k+1)} &= &Ux^{(k)}+b
\end{array}$$
espandendo le matrici si ottiene
![[Pasted image 20230510232155.png]]
 
e da qui possiamo riscrivere l equazione per calcolare la $i$-esima riga come 

_moltiplicando_ le matrici scopro che vale
$$\begin{array}{}
\sum^i_{{j=1}}a_{ij}x_{j}=b_{i}- \sum_{j=i+1}^{n}a_{ij}x_{j}
\end{array}$$
- la prima sommatoria perché la matrice di destra è triangolare inferiore. la seconda perché è triangolare superiore.

da qui posso togliere l elemento $i$-esimo della prima sommatoria e ottenere
$$\begin{array}{}
a_{ii}x_{i}+ \sum^{i-1}_{j=1}a_{ij}x_{j} & = & b_{i}- \sum_{j=i+1}^{n}a_{ij}x_{j} \\
a_{ii}x_{i} & = & b_{i}- \sum^{i-1}_{j=1}a_{ij}x_{j}- \sum_{j=i+1}^{n}a_{ij}x_{j}
\end{array}
$$
$$$$
e divenendo per $a_{ii}$ ottengo
$$x_i^{(k+1)}= \frac{1}{a_{ii}}\left[ b_{i} - \sum^{i-1}_{j=1} a_{ij}x_j^{(k+1)}- \sum^{n}_{j=i+1}a_{ij}x_j^{(k)} \right]$$
- Posso dividere per $a_{ii}$ siccome assumo che siano _diversi_ da $0$ nelle ipotesi di applicabilità 