---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Convergenza locale per metodi interativi funzionali
---
formalmente la convergenza locale è definita come

sia $g:[a,b]\rightarrow \mathbb{R} , \ \ \alpha = g(\alpha), \ \ \ \alpha \in (a,b)$ il metodo
$$\begin{cases}
x_{0} \in [a,b] \\
k_{k+1} = g(x_{k})
\end{cases}$$
_converge localmente_ se $\exists \rho>0: \forall x_{0}\in [\alpha-\rho,\alpha+\rho]$.
se scelgo un puto in questo intervallo ottengo che
1. $x_{k}\in [\alpha-\rho,\alpha+\rho]\  \forall k\geq 0$ ovvero, _tutti_ i valori della successione restano nel intervallo
2. $\lim_{ k \to \infty }x_{k}=\alpha$ 