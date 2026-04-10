---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Sottospazi affini
---
_sia_ $V$ un [[Spazi Vettoriali]] e $W \subset V$ un [[Sottospazio Vettoriale|sotto spazio vettoriale]]
_allora_ un _sotto spazio affine_ di $V$ e un insieme $S$ [[Soluzioni di un sistema lineare|delle soluzioni]] di un [[Sistemi lineari e lineari omogenei|sistema lineare]] tale che

$$
S= \{ x+v\mid v\in W \}
$$

e per indicare un sotto spazio affine si usa la _notazione implicita_

$$
S=x+W=\{ x+v\mid v \in W \}
$$

#### Teoria
lo stesso _sottospazio affine_ puo essere descritto in io modi diversi infatti

##### Proposizione
_siano_ $x+W$ e $x'+W'$ due _spazzi affini_
_allora_ questi _coincidono_ se e solo se

$$
W=W' \ \ e \ \ x-x' \in W
$$

**Esempio 3.2.5.** Se

$$
W = \operatorname{Span}\begin{pmatrix}1\\1\end{pmatrix}
$$

in $\mathbb{R}^2$, le due rette affini

$$
r_1 = \begin{pmatrix}1\\0\end{pmatrix} + W = \left\{ \begin{pmatrix}1+t\\t\end{pmatrix} \mid t \in \mathbb{R} \right\},
$$

$$
r_2 = \begin{pmatrix}0\\-1\end{pmatrix} + W = \left\{ \begin{pmatrix}u\\u-1\end{pmatrix} \mid u \in \mathbb{R} \right\}
$$

sono in realta la stessa retta di equazione $y = x - 1$.

Nella descrizione di uno spazio affine $S$ come $x + W$, lo spazio vettoriale $W$ e determinato da $S$ ed e detto la _giacitura_ di $S$. Il punto $x$ invece e un qualsiasi punto di $S$.

**Definizione 3.2.6.** La _dimensione_ di $S$ e la dimensione della giacitura $W$.

#### Esempi di spazzi affini
Un _sottospazio affine_ di [[Dimensione di uno spazio vettoriale|dimensione]] 0 e un qualsiasi punto di $V$. Un sottospazio affine di dimensione $1$ e detto *retta affine* e di dimensione $2$ e detto _piano affine_. lo spazio $\mathbb{R}^3$ contiene ovviamente _infinite_ rette affini e _infiniti_ piani affini.
