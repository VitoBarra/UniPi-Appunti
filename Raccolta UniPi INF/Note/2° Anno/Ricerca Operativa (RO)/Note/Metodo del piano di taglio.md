---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Metodo del piano di taglio
---

## Diseguaglianza valida

una disequazione e detta disuguaglianza valida (DV) per l’insieme $\Omega$ se

$$
p^T x \leq p_0 \ \ \ \
\forall x \in \Omega.
$$

### Piano di taglio

Un piano di taglio è una disuguaglianza valida  $p^T x \leq p_0$ per $\Omega$ tale che $p^T \overline{x} > p_0$, dove $\overline{x}$ e l’ottimo del rilassamento continuo.

---

## Metodo del piano di taglio

**se** $P$ e la regione ammissibile del rilassamento continuo e la soluzione ottima $\overline{x}$ di $\max_{x \in P}c^T x$appartiene ad $\Omega$, allora $\overline{x}$ e ottima anche per $\max_{x \in \Omega} c^T x$
**altrimenti** si costruisce un piano di taglio $p^T x \leq p_0$  in modo da tagliare fuori $\overline{x}$ e poi
risolvere il nuovo problema di PL:

$$
\begin{cases}
\max c^Tx \\
x \in P \\
p^T \leq p_0
\end{cases}
$$

---

## Piani di taglio di Gomory

Supponiamo che il problema di [[Programmazione lineare Intera|PLI]] sia nella forma

$$
\begin{cases}
\max c^Tx \\
Ax = b \\
x \geq 0 \\
x \in \mathbb{Z}^n
\end{cases}
$$

e per $\overline{x}$ sia una soluzione di base (relativa alla [[Basi e vertici|base]] $B$) ottima del rilassamento continuo di P. poniamo

$$
A = (A_B,A_N)
\ \ \ \ \ \ \ \
\overline{x} = \begin{pmatrix}
x_B \\
x_N
\end{pmatrix}
\ \ \ \ \ \ \ \ \
\tilde{A} = A^{-1}_BA_N
\ \ \ \ \ \ \ \ \
\tilde{b} = \overline{x}_B
$$

Se esiste un indice $r \in B$ tale che $\tilde{b}_r \not\in \mathbb{Z}$ , allora

$$
\sum_{j\in N}\{\tilde{a}_{rj}\}x_j \geq  \{\tilde{b}_r\}
$$

è un piano di taglio detto di Gomory per il problema. dove $\{ \cdot \}$ è la parte frazionaria

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 26.png]]

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 20.png]]

![[Untitled 2 13.png]]
