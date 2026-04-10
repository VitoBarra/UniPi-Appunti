---
Course: "[[Algebra Lineare (AL)]]"
topic:
tags:
  - AL
---

# Sottospazio Ortogonale
---

### Definizione

dato uno spazio ortogonale $V$ e sia $W \subset V$ un [[Sottospazio Vettoriale]] il sottospazio ortogonale $W^\bot$ e definito come

$$
W^\bot =\{v\in V\ |\ \langle v,w\rangle = 0 \ \ \forall w \in W \}
$$

### Proprietà:

- se il [[Prodotto Scalare]] e definito positivo allora sono $W,W^\bot$ in somma diretta
- se il [[Prodotto Scalare]] e degenere, puo accadere che $W^\bot$ abbia dimensione maggiore delle aspettative intuitive

Se $v \in \mathbb{R}^n$, allora

$$
\langle v \rangle^\bot = \{u \in \mathbb{R}^n \mid \langle u, v \rangle = 0\}.
$$

$\langle v \rangle^\bot$ e detto sottospazio ortogonale a $v$.

Se

$$
v = (a_1, \dots, a_n),
$$

allora $\langle v \rangle^\bot$ e l'insieme delle soluzioni di

$$
a_1x_1 + \cdots + a_nx_n = 0,
$$

utile per trovare una base.

### Più vettori

Se $v_1, \dots, v_r \in \mathbb{R}^n$ e

$$
f_{v_i}(w) = \langle w, v_i \rangle,
$$

allora

$$
\langle v_1, \dots, v_r \rangle^\bot
= \{w \in \mathbb{R}^n \mid \langle v_1, w \rangle = \cdots = \langle v_r, w \rangle = 0\}
$$

$$
= \{w \in \mathbb{R}^n \mid \forall v \in \operatorname{Span}(v_1, \dots, v_r),\ \langle v, w \rangle = 0\}
$$

$$
= \ker(f_{v_1}) \cap \cdots \cap \ker(f_{v_r}).
$$

Ovvero, se

$$
v_i = (a_{i1}, \dots, a_{in}),
$$

allora e l'insieme delle soluzioni del sistema omogeneo:

$$
\begin{cases}
a_{11}x_1 + \cdots + a_{1n}x_n = 0 \\
\vdots \\
a_{r1}x_1 + \cdots + a_{rn}x_n = 0
\end{cases}
$$

Questa definizione e valida perche se

$$
v = \alpha_1 v_1 + \cdots + \alpha_r v_r,
$$

allora

$$
\langle v, w \rangle = \alpha_1 \langle v_1, w \rangle + \cdots + \alpha_r \langle v_r, w \rangle,
$$

quindi se $w$ e perpendicolare a $v_1, \dots, v_r$, tutti i prodotti scalari valgono $0$ e anche $\langle v, w \rangle = 0$.

### Interpretazione geometrica

Il sottospazio ortogonale e un $k$-piano passante per l'origine e perpendicolare a $\operatorname{Span}(v_1, \dots, v_r)$.

### Sottospazio ortogonale ad uno spazio vettoriale

Dato lo spazio vettoriale

$$
V \subseteq \mathbb{R}^n,
$$

si definisce

$$
V^\bot = \{w \in \mathbb{R}^n \mid \forall v \in V,\ v \cdot w = 0\}.
$$

Vale che

$$
V \cap V^\bot = \{0\},
\qquad
\operatorname{Span}(V, V^\bot) = \mathbb{R}^n,
\qquad
\dim(V) + \dim(V^\bot) = n.
$$

### Vettori e sistemi ortogonali

$v, w \in \mathbb{R}^n$ si dicono ortogonali se

$$
v \cdot w = 0.
$$

$v_1, \dots, v_r$ e un sistema ortogonale se non contiene vettori nulli e se per ogni $i \neq j$ vale

$$
v_i \cdot v_j = 0.
$$

E un sistema ortonormale se vale anche, per ogni $i$,

$$
v_i \cdot v_i = 1.
$$

Un sistema ortogonale e linearmente indipendente.
