---
Subject: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---

# Soluzioni di un sistema lineare
---
l [[Insiemi Matematici|insieme]] delle _soluzioni_ $S$ di un [[Sistemi lineari e lineari omogenei|sistema lineare]] se $S \not= \{0\}$ si può descrivere a partire da un suo elemento  $x \in S$ chiamata _soluzione particolare_  e sommando tutto i vettori di $S_0$ ovvero le soluzioni del sistema _lineare omogeneo_ associato

### Teorema
_Sia_ $\mathcal{S}$ l [[Insiemi Matematici|insieme]] delle _soluzioni_ di un [[Sistemi lineari e lineari omogenei|sistema lineare]] e $S_0$ l insieme delle _soluzioni_ del sistema lineare associato a quel [[Sistemi lineari e lineari omogenei|sistema lineare]]
_Se_ $S \not= ∅$, 
_allora_ $S$ è ottenuto prendendo una qualsiasi soluzione e aggiungendo a questa tutti i vettori di $S_0$.

#### Dimostrazione 
sia $x \in S$ una _soluzione del sistema lineare_ e $x’ \in S_0$ una soluzione del _sistema lineare omogeneo associato_. si vede facilmente che $x+x’$ è anche essa soluzione del primo sistema, infatti
$$a_{i1}(x_1+x_1’) + \cdots+a_in(x_n+x_n’) = b_1+0=b_i$$
Se in vece $x’’$ è soluzione del primo sistema . allora $x’ = x’’-x$ è soluzione del secondo sistema perché 
$$a_{i1}(x_1’’-x_1’) + \cdots+a_{in}(x_n’’-x_n’) = b_i-b_i=0$$
quindi la soluzione del primo sistema si ottengono tutte precisamente aggiungendo ad un fissato $x \in S$ le soluzioni $x’ \in S_0$ del secondo sistema 









> [!example] 
Consideriamo il sistema in $\mathbb{R}^3$
> $$\begin{cases}
x-y+z  & = & 1 \\y-z  & = &  2
\end{cases}$$
> Risolvendo troviamo che le soluzioni $S$ sono del tipo
> $$
\begin{pmatrix}3\\t\\t-2 \end{pmatrix} =
\begin{pmatrix} 3\\0\\-2\end{pmatrix} +
\begin{pmatrix}0\\t\\t\end{pmatrix}$$
> al variare di $t \in \mathbb{R}$. Le soluzioni $S_0$ del sistema omogeneo associato
$$
\begin{cases}
x-y+z =0\\
\ \ \ \ \ \ \  y-z = 0
\end{cases}
$$

sono precisamente i vettori del tipo

$$
\begin{pmatrix}
0 \\u \\u
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
