---
type: nota
course: Algebra Lineare
topic: 
tags:
  - AL
Parent MOC: "[[Algebra Lineare (AL)]]"
---
# Spazi vettoriali in somma diretta
---

_Sia_ $V$ uno [[Spazio Vettoriale]] e  $U, W \subset V$ due [[Sottospazio Vettoriale|sottospazi]] 
_se_ $U ∩ W = \{0\}$
_allora_ sono in _somma diretta_

In questo caso indichiamo la loro somma come $$U \oplus W$$ e utilizzando la _[[Formula di Grassman|formula di Gassman]]_ otteniamo che la [[Dimensione di uno spazio vettoriale|dimensione]] di questo spazio $$
\dim( U \oplus W) = \dim(U) + \dim(W)
$$
le espressioni qui sotto sono modi equivalenti per esprimere $V = U \oplus W$

- $V = U \oplus W$
- $dim (V)= dim(U+W) = dim(U)+dim(W)$
    - $V = U +W$
    - $U \cap W = \{0\}$
- Per qualsiasi scelta di basi $u_1,\dots, u_k$ di $U$ e $w_1,\dots, w_h$  di $W$, l’unione  $u_1,\dots, u_k , w_1,\dots, w_h$ è una base di $U + W$
- Ogni vettore $v ∈ V$ si scrive in modo unico come $v = u + w$ per
qualche $u ∈ U$  e $w ∈ W$

>[!info] Osservazione
> queste equivalenze si possono espandere al caso in cui i sottospazi siano $k$

Esempi:
- $U,W \subset \mathbb{R}^2 \land U \cap W =\{0\} \implies \mathbb{R}^2 = U\oplus W$
- $U \subset \mathbb{R}^2 \land W\subset \mathbb{R}^3 \land U \cap W =\{0\} \implies \mathbb{R}^3 = U\oplus W$
- $S(n) \oplus A(n) =M(n)$
