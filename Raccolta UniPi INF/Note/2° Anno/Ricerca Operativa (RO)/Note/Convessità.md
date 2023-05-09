---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Convessità
---

### Combinazione convessa

Siano dei vettori $x_1,\dots,x_m \in \mathbb{R}^n$ un vettore $x \in \mathbb{R}^n$ è detto combinazione convessa se esistono coefficienti $\lambda_1,\dots,\lambda_m \in [0,1]$ con $\sum_{i=1}^m\lambda_i=1$, tale che

$$
x =\sum_{i=1}^m \lambda_ix_i
$$

la combinazione convessa è proprio se $\lambda_1,\dots,\lambda_m \in (0,1)$ impropria altrimenti

---

### Insieme Convesso
Un insieme $K \subseteq \mathbb{R}^n$ è detto convesso se vale

$$
\begin{array}
\lambda x+(1-\lambda)y \in \mathbb{K}  \\

\forall x,y \in \mathbb{K}  \land
\forall \lambda \in [0,1]
\end{array}
$$

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 23.png]]

---

### Involucro Convesso

L’involucro convesso di un insieme $K \subset \mathbb{R}^n$, denotato con $conv(K)$ , è l’insieme di
tutte le combinazioni convesse di punti di $K$

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 18.png]]
