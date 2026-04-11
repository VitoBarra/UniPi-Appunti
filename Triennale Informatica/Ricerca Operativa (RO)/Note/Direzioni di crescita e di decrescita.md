---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---


# Direzioni di crescita e di decrescita
Considerato il seguente problema di [[Programmazione lineare|PL]] in forma canonica $$
\begin{cases}
\max c^Tx\\
Ax \leq b
\end{cases}
$$
- un vettore $d$ è detto **direzione di crescita** per la funzione obbiettivo di $(\mathcal{P})$ se $c^Td>0$
- un vettore $d$ è detto **direzione di decrescita** per la funzione obbiettivo di $(\mathcal{P})$ se $c^Td<0$
la funzione obiettivo cresce o decresce lungo la semirette di direzione $d$:$$c^T(x+\lambda d) = c^Tx+\lambda c^Td \rightarrow \pm \infty\lim \lambda \rightarrow \pm\infty$$