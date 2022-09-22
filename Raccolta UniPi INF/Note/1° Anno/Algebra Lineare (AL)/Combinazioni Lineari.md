---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Combinazioni Lineari
---

### Definizione
Sia $V$ uno spazio vettoriale qualsiasi. Siano $v_1, \dots , v_k ∈ V$ dei vettori arbitrari. Una combinazione lineare dei vettori $v_1, \dots, v_k$ è un qualsiasi vettore v che si ottiene come

$$
v = \lambda_1v_1 + \cdots + \lambda_k v_k
$$

dove $\lambda_1,\dots, \lambda_k$ sono scalari arbitrari.

### Esempi:

sia

$$
V = \R^3 \ \ \ \ \
v_1 =
\begin{pmatrix}
1 \\
0 \\
0
\end{pmatrix} \ \ \ \
v_2 =
\begin{pmatrix}
0 \\
1 \\
0
\end{pmatrix}
$$

allora una combinazione lineare arbitraria di questi due vettori è il vettore

$$
\lambda_1v_1  + \lambda_2 v_2 = \lambda_1
\begin{pmatrix}
1 \\
0 \\
0
\end{pmatrix} +
\lambda_2
\begin{pmatrix}
0 \\
1 \\
0
\end{pmatrix}  =
\begin{pmatrix}
\lambda_1 \\
0 \\
0
\end{pmatrix}+
\begin{pmatrix}
0 \\
\lambda_2 \\
0
\end{pmatrix} =
\begin{pmatrix}
\lambda_1 \\
\lambda_2 \\
0
\end{pmatrix}
$$

Osservazione: questo vettore sta nel piano orizzontale $z = 0$. Osserviamo
anche che al variare di $\lambda_1$ e $\lambda_2$, facendo tutte le combinazioni lineari di $v_1$ e
$v_2$ otteniamo precisamente tutti i punti del piano orizzontale $z = 0$.

---

### Span

siano $v_1,\dots,v_n \in V$ dei vettori l insieme di tutte le combinazioni lineare di questi si chiama



$$
Span(v_1,\dots,v_n)
$$
