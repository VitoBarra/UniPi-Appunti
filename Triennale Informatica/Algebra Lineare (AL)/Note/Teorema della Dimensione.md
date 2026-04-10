---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---

# Teorema della Dimensione
---

### Definizione
Sia $f : V \rightarrow W$ una [[Applicazioni Lineari|applicazione lineare]]. Se $V$ ha [[Dimensione di uno spazio vettoriale|dimensione]] finita $n$, allora

$$
\dim(\ker(f)) + \dim(\operatorname{Im}(f)) = n.
$$

**Esempio 4.2.10.** Nella proiezione $p_U : V \to U$ definita a partire da una somma diretta

$$
V = U \oplus W,
$$

troviamo

$$
\ker p_U = W,
\qquad
\operatorname{Im} p_U = U.
$$

Quindi

$$
V = U \oplus W = \operatorname{Im} p_U \oplus \ker p_U
$$

e

$$
\dim V = \dim \operatorname{Im} p_U + \dim \ker p_U.
$$

### Caratterizzazione iniettiva e suriettiva

**Corollario 4.2.14.** Sia $f : V \to W$ un'applicazione lineare. Vale

$$
\dim \operatorname{Im} f \leq \dim V.
$$

Inoltre:

1. $f$ e iniettiva $\iff \dim \operatorname{Im} f = \dim V$.
2. $f$ e suriettiva $\iff \dim \operatorname{Im} f = \dim W$.

Un altro criterio utile e il seguente: se $v_1, \dots, v_n$ e una base per $V$, allora valgono i fatti seguenti:

- $f$ iniettiva $\iff f(v_1), \dots, f(v_n)$ sono indipendenti.
- $f$ suriettiva $\iff f(v_1), \dots, f(v_n)$ generano $W$.

**Esempio 4.2.16.** Sia $A \in M(m,n,\mathbb{K})$. La funzione $L_A : \mathbb{K}^n \to \mathbb{K}^m$ e

- iniettiva $\iff \operatorname{rk} A = n$,
- suriettiva $\iff \operatorname{rk} A = m$.

### Corollari interessanti:

**Corollario 4.2.23.** Sia $f : V \to W$ un'applicazione lineare.

1. Se $f$ e iniettiva, allora $\dim V \leq \dim W$.
2. Se $f$ e suriettiva, allora $\dim V \geq \dim W$.
3. Se $f$ e un isomorfismo, allora $\dim V = \dim W$.

La proposizione seguente e analoga alle Proposizioni 2.3.23 e 2.3.29, ed e utile concretamente per dimostrare che una data $f$ e un isomorfismo.

**Proposizione 4.2.24.** Sia $f : V \to W$ un'applicazione lineare. Se

$$
\dim V = \dim W,
$$

allora i fatti seguenti sono equivalenti:

1. $f$ e iniettiva,
2. $f$ e suriettiva,
3. $f$ e un isomorfismo.

Dimostrazione. Per il teorema della dimensione, se

$$
n = \dim V = \dim W,
$$

allora

$$
f \text{ iniettiva } \iff \dim \ker f = 0 \iff \dim \operatorname{Im} f = n \iff f \text{ suriettiva}.
$$

**Proposizione 4.2.28.** Siano $f : V \to W$ e $g : W \to Z$ lineari. Allora:

- $\dim \operatorname{Im}(g \circ f) \leq \min\{\dim \operatorname{Im} g, \dim \operatorname{Im} f\}$.
- Se $f$ e un isomorfismo, allora $\dim \operatorname{Im}(g \circ f) = \dim \operatorname{Im} g$.
- Se $g$ e un isomorfismo, allora $\dim \operatorname{Im}(g \circ f) = \dim \operatorname{Im} f$.

**Proposizione 4.2.29.** Siano $A$ e $B$ due matrici che si possono moltiplicare. Valgono i fatti seguenti:

- $\operatorname{rk}(AB) \leq \min\{\operatorname{rk} A, \operatorname{rk} B\}$.
- Se $A$ e invertibile, allora $\operatorname{rk}(AB) = \operatorname{rk} B$.
- Se $B$ e invertibile, allora $\operatorname{rk}(AB) = \operatorname{rk} A$.

Dimostrazione. Segue dalla Proposizione 4.2.28 applicata a $L_A$ e $L_B$.
