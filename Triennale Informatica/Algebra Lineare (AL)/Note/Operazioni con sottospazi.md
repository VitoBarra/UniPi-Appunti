---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags: AL
---
# Operazioni con sottospazii
---
i [[Sottospazio Vettoriale|sottospazii vettoriali]] sono insiemi e a questi insiemi possono essere applicate le normali operazioni insiemistiche
quindi le operazioni su due [[Sottospazio Vettoriale]] $U,W \subset V$
- unione $\cup$  : dove $U \cup V \not\subset V$ quasi sempre
- intersezione $\cap$ : dove $U \cap V \subset V$ sempre
- somma $+$ : dove $U + V \subset V$ sempre
considerazioni utili:

$$
U = Span(u_1...u_n)\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ W = Span(w_1...w_n)
$$

$$
U+W = Span(u_1...u_n,w_1...w_n)
$$

## Calcolo del intersezione:

Esempio.

Siano

$$
\pi_1 = \left\langle \begin{pmatrix}1\\1\\0\end{pmatrix}, \begin{pmatrix}0\\1\\1\end{pmatrix} \right\rangle,
\qquad
\pi_2 = \left\langle \begin{pmatrix}1\\1\\-1\end{pmatrix}, \begin{pmatrix}1\\0\\-1\end{pmatrix} \right\rangle \subseteq \mathbb{K}^3.
$$

Vogliamo trovare una base di $\pi_1 \cap \pi_2$.

$\pi_1 \cap \pi_2$ consiste dei vettori di $\mathbb{K}^3$ che sono simultaneamente combinazione lineare dei generatori di $\pi_1$ e dei generatori di $\pi_2$.

Quindi vogliamo capire per quali scalari $x, y, z, w$ si ha:

$$
x \begin{pmatrix}1\\1\\0\end{pmatrix}
+ y \begin{pmatrix}0\\1\\1\end{pmatrix}
= z \begin{pmatrix}1\\1\\-1\end{pmatrix}
+ w \begin{pmatrix}1\\0\\-1\end{pmatrix}
$$

cioe

$$
x \begin{pmatrix}1\\1\\0\end{pmatrix}
+ y \begin{pmatrix}0\\1\\1\end{pmatrix}
- z \begin{pmatrix}1\\1\\-1\end{pmatrix}
- w \begin{pmatrix}1\\0\\-1\end{pmatrix}
= 0.
$$

Consideriamo questa equazione come un sistema lineare e applichiamo l'eliminazione:

$$
\begin{pmatrix}
1 & 0 & -1 & -1 \\
1 & 1 & -1 & 0 \\
0 & 1 & 1 & 1
\end{pmatrix}
\xrightarrow{R_2 \to R_2 - R_1}
\begin{pmatrix}
1 & 0 & -1 & -1 \\
0 & 1 & 0 & 1 \\
0 & 1 & 1 & 1
\end{pmatrix}
\xrightarrow{R_3 \to R_3 - R_2}
\begin{pmatrix}
1 & 0 & -1 & -1 \\
0 & 1 & 0 & 1 \\
0 & 0 & 1 & 0
\end{pmatrix}.
$$

Le soluzioni sono date da $z = 0$, $y = -w$ e $x = z + w = w$, quindi

$$
x \begin{pmatrix}1\\1\\0\end{pmatrix}
+ y \begin{pmatrix}0\\1\\1\end{pmatrix}
= z \begin{pmatrix}1\\1\\-1\end{pmatrix}
+ w \begin{pmatrix}1\\0\\-1\end{pmatrix}
$$

diventa

$$
x \begin{pmatrix}1\\1\\0\end{pmatrix}
+ y \begin{pmatrix}0\\1\\1\end{pmatrix}
= -w \left( \begin{pmatrix}0\\1\\1\end{pmatrix} - \begin{pmatrix}1\\1\\0\end{pmatrix} \right)
= w \begin{pmatrix}1\\0\\-1\end{pmatrix}.
$$

Questo mostra che

$$
\begin{pmatrix}1\\0\\-1\end{pmatrix} \in \pi_1 \cap \pi_2,
$$

quindi

$$
\left\langle \begin{pmatrix}1\\0\\-1\end{pmatrix} \right\rangle \subseteq \pi_1 \cap \pi_2,
$$

e che ogni vettore di $\pi_1 \cap \pi_2$ e un multiplo di

$$
\begin{pmatrix}1\\0\\-1\end{pmatrix}.
$$

Concludiamo che

$$
\pi_1 \cap \pi_2 = \left\langle \begin{pmatrix}1\\0\\-1\end{pmatrix} \right\rangle
$$

con base data da

$$
\begin{pmatrix}1\\0\\-1\end{pmatrix}.
$$
