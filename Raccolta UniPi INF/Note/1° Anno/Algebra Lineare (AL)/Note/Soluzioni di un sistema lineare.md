---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Soluzioni di un sistema lineare
---

### Definizione
l insieme delle soluzioni $S$ di un [[Sistemi lineari e lineari  omogenei|sistema lineare]] se $S \not= \{0\}$ si può descrivere a partire da un suo elemento  $x \in S$ chiamata soluzione particolare  e sommando tutto i vettori di $S_0$ ovvero le soluzioni del sistema lineare omogeneo associato

Se $S \not= ∅$, allora $S$ è ottenuto prendendo una qualsiasi soluzione  e aggiungendo a questa tutti i vettori di $S_0$.

#### Dimostrazione 
sia $x \in S$ una soluzione del sistema e $x’ \in S_0$ una soluzione del sistema. si vede facilmente che $x+x’$ è anche essa soluzione del primo sistema, infatti
$$a_{i1}(x_1+x_1’) + \cdots+a_in(x_n+x_n’) = b_1+0=b_i$$
Se in vece $x’’$ è soluzione del primo sistema . allora $x’ = x’’-x$ è soluzione del secondo sistema perché 
$$a_{i1}(x_1’’-x_1’) + \cdots+a_{in}(x_n’’-x_n’) = b_i-b_i=0$$
quindi la soluzione del primo sistema si ottengono tutte precisamente aggiungendo ad un fissato $x \in S$ le soluzioni $x’ \in S_0$ del secondo sistema 





### esempio:
Consideriamo il sistema in $\R^3$

$$
\begin{cases}
x-y+z =1 \\
\ \ \ \ \ \ \  y-z = 2
\end{cases}
$$

Risolvendo troviamo che le soluzioni $S$ sono del tipo

$$
\begin{pmatrix}
 3\\t\\t-2
\end{pmatrix} =
\begin{pmatrix}
 3\\0\\-2
\end{pmatrix} +
\begin{pmatrix}
 0\\t\\t
\end{pmatrix}
$$

al variare di $t \in \R$. Le soluzioni $S_0$ del sistema omogeneo associato

$$
\begin{cases}
x-y+z =0\\
\ \ \ \ \ \ \  y-z = 0
\end{cases}
$$

sono precisamente i vettori del tipo

$$
\begin{pmatrix}
0 \\t \\t
\end{pmatrix}
$$

Le soluzioni in $S$ sono tutte ottenute prendendo la soluzione particolare

$$
\begin{pmatrix}
3 \\0 \\-2
\end{pmatrix}
$$

ed aggiungendo a questa tutte le soluzioni in $S_0$ del sistema omogeneo associato. qualsiasi elemento di $S$ può fungere da soluzione particolare: ad esempio potremmo prendere

$$
\begin{pmatrix}
3 \\2 \\0
\end{pmatrix}
$$

e quindi descrivere lo stesso insieme $S$ di soluzioni in questo modo

$$
\begin{pmatrix}
3\\2\\0
\end{pmatrix} +
\begin{pmatrix}
0\\u\\u
\end{pmatrix} =
\begin{pmatrix}
3\\2+u\\u
\end{pmatrix}

$$

Si ottiene effettivamente lo stesso insieme $S$ di prima, sostituendo $t = u+2$
