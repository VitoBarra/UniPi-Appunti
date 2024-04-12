---
Subject: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Mosse di gauss
---
_sia_ la $C_i$ la $i-esima$ riga di una [[Matrice|matrice]] possiamo fare le seguenti _mosse di guass_  senza modificare l [[Soluzioni di un sistema lineare|insieme delle soluzioni]] $\mathcal{S}$ del [[Sistemi lineari e lineari omogenei|sistema]]. 
1. $C_{i}\leftrightarrow C_{j}$
	1. Scambiare due righe
2. $C_{i}\rightarrow \lambda C_{i}, \lambda \not = 0$
	1. moltiplicare una riga per un numero $\lambda \not=0$
3. $C_{i}\rightarrow \lambda C_{i}+\lambda C_{j}$
	1. aggiungere ad una riga un altra riga moltiplicato per  un $\lambda$ qualsiasi 

Per ogni riga $C_i$ di $C$, chiamiamo _pivot_ il primo elemento non nullo della riga $C_i$. Una matrice a scalini è una matrice avente la proprietà seguente: il pivot di ogni riga è sempre strettamente più a _destra_ del pivot della riga precedente



> [!example]-  Esempi di matrici a scalini
> $$
\begin{pmatrix}
1 & 0 &5 \\
0 & -1 & -1
\end{pmatrix} \ \ \
\begin{pmatrix}
7 &-2 & 9 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{pmatrix}
>$$
>mentre invece _non_ sono metrici a scalini:
>$$
\begin{pmatrix}
1 & 2 & -1 \\
4 & 0 & 6 \\
0 & 7 & 0
\end{pmatrix} \ \ \
\begin{pmatrix}
0 & 8 \\
0 & 1 \\
0 & 0 \\
0 & 0
\end{pmatrix}
$$

#### Matrice Gauss - jordan
i pivot hanno sopra e sotto degli 0

da teneri in considerazione quando si risolve un sistema con Gauss - Jordanci sono due casi da considerare.

Se la colonna dei termini noti $b$ contiene un pivot, allora la matrice è indicativamente di questo tipo:
$$\begin{bmatrix} & 
\begin{array}{cccccc|c}
0 & 1 & ? & 0 & 0 & ?  & ? \\
0 & 0 & 0 & 1 & 0 & ?  & ? \\
0 & 0 & 0 & 0 & 0 & 0  & 1
\end{array} & 
\end{bmatrix}
$$
la riga che contiene l ultimo _pivot_ rappresenta l equazione $0=1$ che non ha soluzione. in questo caso l insieme delle soluzioni è vuoto $\mathcal{S}=\emptyset$

considerando il caso in cui l ultimo colonna non contenga pivot. la matrice $C$ è indicativamente in questo tipo:
$$\begin{bmatrix} & 
\begin{array}{cccccc|c}
0 & 1 & a_{13} & 0 & 0 & a_{16}  & b_{1} \\
0 & 0 & 0 & 1 & 0 & a_{26}  & b_{2}  \\
0 & 0 & 0 & 0 & 0 & a_{36}  & b_{3}
\end{array} & 
\end{bmatrix}
$$
allora questa ha infinite soluzioni


