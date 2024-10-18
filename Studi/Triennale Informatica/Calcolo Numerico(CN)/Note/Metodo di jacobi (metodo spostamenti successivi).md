---
Course: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodo di jacobi (metodo spostamenti successivi)
---
è un [[Metodi Iterativi per soluzioni di sistemi lineari|metodo iterativo]] basato su decomposizione di $A$ per il calcolo di una [[Soluzioni di un sistema lineare|soluzione di un sistema lineare]].
fattorizziamo $A = M - N$ con
- $M=D$ 
- $N=L+U$ 
- la mia matrice di interazione $J =D^{-1}(L+U)$
dove $A=$
![[Pasted image 20230510215538.png]]

>[!warning]
>posso applicare questo metodo solo alle matrici con $a_{ii} \not= 0\ \ \ \forall i =1,\dots,n$ ovvero solo a quelle matrici che _NON_ hanno elementi nulli sulla _diagonale_. cosi non fosse $D$ non sarebbe [[Matrice inversa|invertibile]].

quindi il _metodo_ diventa
$$\begin{cases}
x^{(0)} \in \mathbb{K}^n\\
x^{(k+1)} = Jx^{(k)}+D^{-1}b
\end{cases}$$
Possiamo pero riscrivere la seconda espressione come
$$
\begin{array}{}
x^{(k+1)} &=& Jx^{(k)}+D^{-1}b \\
x^{(k+1)} &= &D^{-1}((L+U)x^{(k)}+b)  \\
Dx^{(k+1)} &= &Lx^{(k)}+Ux^{(k)}+b
\end{array}$$
espandendo le matrici si ottiene
![[Pasted image 20230510223010.png]]
da qui possiamo valutare ogni elemento $i-$esimo di $x$ moltiplicando le matrici e ottenendo
$$a_{ii}x_i^{(k+1)}= b_{i} - \sum^{i-1}_{j=1} a_{ij}x_{j}^{(k)}- \sum^{n}_{j=i+1}a_{ij}x_j^{(k)} $$
e da questo possiamo scrivere la relazione 
$$x_i^{(k+1)}= \frac{1}{a_{ii}}\left[ b_{i} - \sum^{i-1}_{j=1} a_{ij}x_{j}^{(k)}- \sum^{n}_{j=i+1}a_{ij}x_j^{(k)} \right]$$
- Posso dividere per $a_{ii}$ siccome assumo che siano _diversi_ da 0