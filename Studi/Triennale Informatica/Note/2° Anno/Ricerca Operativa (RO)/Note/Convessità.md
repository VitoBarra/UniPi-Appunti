---
course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---


# Convessità
---

### Combinazione convessa

Siano $\boldsymbol{x}_1,\dots,\boldsymbol{x}_m \in \mathbb{R}^n$ dei [[Vettori|vettori]]  
se esistono coefficienti $\lambda_1,\dots,\lambda_m \in [0,1]$ con $\sum_{i=1}^m\lambda_i=1$, tale che$$
x =\sum_{i=1}^m \lambda_ix_i
$$Allora un vettore $\boldsymbol{x} \in \mathbb{R}^n$ è detto combinazione convessa 

la combinazione convessa è detta
- proprio se $\lambda_1,\dots,\lambda_m \in (0,1)$
- impropria  se $\lambda_1,\dots,\lambda_m \not\in (0,1)$

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

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 23.png]]

---

### Involucro Convesso

L’involucro convesso di un insieme $K \subset \mathbb{R}^n$, denotato con $conv(K)$ , è l’insieme di
tutte le combinazioni convesse di punti di $K$

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 18.png]]
