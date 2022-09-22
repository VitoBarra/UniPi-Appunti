---
type: nota
course: Algebra Lineare
topic: 
tags: AL ToReview
---

Prev: [[Algebra Lineare (AL)]]

# Dimensione
---

### Definizione
la dimensione di uno spazio vettoriale è il numero di elementi che ha la sua base, se lo spazio non ha una base allora la sua dimensione è $\infty$



Esempi:

- $dim(K^n)=n$
- $dim(K_n[x]) =n+1$
- $dim(M(m,n,K)) =n \times m$
- $dim(V) =\infty$  se $V$ non ha base

## Teoremi importanti:

Due basi dello stesso spazio vettoriale $V$ hanno lo stesso numero di elementi $n$

Osservazione: questo è il motivo per cui possiamo dire che  $V$  ha un unica dimensione

---

Sia $V$ uno spazio vettoriale e $U \subset V$ un [[sottospazio]]. Vale $0 ≤ dim (U) ≤ dim (V)$. Inoltre:

- $dim (U) = 0 \iff U =\{0\}$
- $dim (U) = dim (V) \iff U =V$

---

### Formula di Gassman:

Sia $V$ uno spazio vettoriale di dimensione finita. Siano $U,W\subset V$ sottospazi. vale la formula

$$
dim(U+W)+dim(U \cap W) = dim(U)+dim(V)
$$

---

### Somma Diretta

Sia $V$ uno spazio vettoriale e  $U, W \subset V$ due sottospazi questi sono in somma diretta

se  $U ∩ W = \{0\}$. In questo caso indichiamo la loro somma con $U ⊕ W$ e Gassman otteniamo

$$
dim( U ⊕ W) = dim(U) + dim(W)
$$

le espressioni qui sotto sono modi equivalenti per esprimere $V = U \oplus W$

- $V = U \oplus W$
- $dim (V)= dim(U+W) = dim(U)+dim(W)$
    - $V = U +W$
    - $U \cap W = \{0\}$
- Per qualsiasi scelta di basi $u_1,\dots, u_k$ di $U$ e $w_1,\dots, w_h$  di $W$, l’unione  $u_1,\dots, u_k , w_1,\dots, w_h$ è una base di $U + W$
- Ogni vettore $v ∈ V$ si scrive in modo unico come $v = u + w$ per
qualche $u ∈ U$  e $w ∈ W$

Osservazione: queste equivalenze si possono espandere al caso in cui i sottospazi siano $k$

Esempi:

- $U,W \subset \R^2 \land U \cap W =\{0\} \implies \R^2 = U\oplus W$
- $U \subset \R^2 \land W\subset \R^3 \land U \cap W =\{0\} \implies \R^3 = U\oplus W$
- $S(n) \oplus A(n) =M(n)$

## lemmi interessanti:

Sia $V$ uno spazio vettoriale su $\mathbb{K}$. Supponiamo di avere:

- dei vettori $v_1, \dots, v_n \in V$ che generano $V$
- dei vettori $w_1,\dots, w_n \in V$ indipendenti

Allora anche i vettori  $w_1, \dots , w_n$  generano $V$

---

ToDo

$S(N) \cap A(n) = \{0\}$
