---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema cinese del resto 
---
_Sia_ dato il sistema di congruenze:
$$
\begin{cases}
x &\equiv a \pmod{n} \\
x &\equiv b \pmod{m}
\end{cases}
$$
dove $a, b, n, m \in \mathbb{Z}$, $n, m > 0$, e $\text{mcd}(n, m) = 1$.
_allora_
1. Il sistema ammette soluzioni.
2. La soluzione generale del sistema è della forma $x = x_0 + M(nm)$, dove $x_0$ è una soluzione particolare ed $M$ varia in $\mathbb{Z}$.

#### Dimostrazione
Evidentemente, le congruenze del sistema hanno singolarmente soluzioni. Sostituendo la soluzione generale della prima congruenza $x = a + nk$, $k \in \mathbb{Z}$, nella seconda:

$a + nk \equiv b \pmod{m} \Rightarrow nk \equiv (b - a) \pmod{m}$

Otteniamo così una congruenza in $k$ che ammette soluzioni perché $1 = \text{mcd}(n, m)$ divide $(b - a)$. Questo dimostra il punto (1). Risolvendo la congruenza in $k$ e sostituendo la soluzione trovata nell'espressione $x = a + nk$, otteniamo tutte e sole le soluzioni della prima congruenza del sistema che sono anche soluzioni della seconda. Ciò fornisce la soluzione generale del sistema. Osserviamo che la soluzione generale della congruenza $nk \equiv (b - a) \pmod{m}$ è della forma $k = k_0 + hm$, dove $k_0$ è una soluzione particolare ed $h$ varia in $\mathbb{Z}$. Di conseguenza, la soluzione generale del sistema risulta essere:

$x = a + n(k_0 + hm) = (a + nk_0) + hnm, \quad h \in \mathbb{Z}$

È immediato verificare che $x_0 = (a + nk_0)$ è una soluzione particolare del sistema. Questo conclude la dimostrazione del punto (2).
