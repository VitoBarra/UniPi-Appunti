---
type: nota
course: Algebra Lineare
topic: 
tags: AL Imm2Text 
---

Prev: [[Algebra Lineare (AL)]]

# Mosse di gauss
---


![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 15.png]]

Per ogni riga $C_i$ di $C$, chiamiamo pivot il primo elemento non nullo della riga $C_i$. Una matrice a scalini è una matrice avente la proprietà seguente: il pivot di ogni riga è sempre strettamente più a
destra del pivot della riga precedente

### esempi di matrici a scalini:

$$
\begin{pmatrix}
1 & 0 &5 \\
0 & -1 & -1
\end{pmatrix} \ \ \
\begin{pmatrix}
7 &-2 & 9 \\
0 & 0 & 1 \\
0 & 0 & 0
\end{pmatrix}
$$

mentre invece non sono metrici a scalini:

$$
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

### Matrice Gauss - Jordan:

i pivot hanno sopra e sotto degli 0

esempio:

$$
\begin{pmatrix}
1&0&4 \\
0&1&1 \\
0&0&0
\end{pmatrix}
$$

da teneri in considerazione quando si risolve un sistema con Gauss - Jordan

![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 9.png]]

allora questa ha infinite soluzioni

### soluzione di un sistema lineare con Gause - jordan:

Rosolviamo il sistema seguente, gia rodotto con l’algoritmo di Gauss-Jordan:

$$
\begin{cases}
x_1+3x_2+4x_5 =1 \\
\ \ \ \ \ \ \ \ \ \ \ x_3-2x_4 =3
\end{cases}
$$

Le variabili corrispondenti ai pivot sono $x_1$ e $x_3$. Le variabili libero sono $x_2,x_4$ e $x_5$. quindi scriviamo

$$
\begin{cases}
x_1 =1 -3t-1 -4t_3 \\
x_2 = t_1 \\
x_3 = 3 +2t_2 \\
x_4 = t_2 \\
x_5 = t_3
\end{cases}
$$


