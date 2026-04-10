---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---
# Sistemi lineari e lineari omogenei
---
Una [[Equazioni Lineari e Lineari omogenee|equazione lineare]] in $n$ variabili $x_1, \dots, x_n$ e' della forma
$$
a_1x_1 + \cdots + a_nx_n = b
$$
dove $a_1, \dots, a_n, b \in \mathbb{K}$.

L'equazione e' __omogenea__ se $b = 0$.

Un punto $x \in \mathbb{K}^n$ e' [[Soluzioni di un sistema lineare|soluzione]] dell'equazione se le sue coordinate $x_1, \dots, x_n$ la soddisfano, cioe' se sostituendole nell'espressione si ottiene proprio $b$.

Un __sistema lineare__ e' un insieme di $k$ equazioni lineari in $n$ variabili messe a [[sistema di equazioni|sistema]]:
$$
\begin{cases}
a_{11}x_1 + \cdots + a_{1n}x_n = b_1 \\
\vdots \\
a_{k1}x_1 + \cdots + a_{kn}x_n = b_k
\end{cases}
$$

Il sistema e' detto __omogeneo__ se $b_1 = \dots = b_k = 0$.

Un punto $x \in \mathbb{K}^n$ e' soluzione del sistema se e' soluzione di ciascuna equazione.

Le soluzioni del sistema formano un certo sottoinsieme
$$
S \subseteq \mathbb{K}^n
$$

Le soluzioni $S \subseteq \mathbb{K}^n$ di un sistema lineare omogeneo formano un [[sottospazio vettoriale|sottospazio vettoriale]] di $\mathbb{K}^n$.

