---
Subject: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Formulazione problema di programmazione di lineare
---

### Definizione
Un problema di [[Programmazione lineare|Programmazione Lineare]] (PL) consiste nel trovare il _massimo_ o il
_minimo_ (e perciò anche detto di ottimizzazione) di una funzione lineare di $n$ variabili reali soggette a vincoli lineari di uguaglianza o di disuguaglianza, detta forma generale oppure in un forma equivalente con solo vincoli di diseguaglianza chiamata forma canonica

### Forma generale

$$
\begin{cases}
\max (o \ \min) \ c^Tx \\
A_1x \leq b_1 \\
A_2x \geq b_1 \\
A_3x = b_3 \\
(x \in \mathbb{R}^n)
\end{cases}
$$

### Forma canonica

$$
\begin{cases}
\max \ c^Tx \\
Ax \leq b \\
(x \in \mathbb{R}^n)
\end{cases}
$$

>[!tip] Equivalenza delle forme
 ogni problema in forma generale puo essere riscritta in forma canonica


### Dimostrazione:

- $\min c^Tx= -\max (-c^Tx)$
- $a^Tx \geq b \iff-a^Tx \leq -b$
- $a^T =b \iff\begin{cases}a^Tx \leq b \\-a^Tx\leq -b\end{cases}$
