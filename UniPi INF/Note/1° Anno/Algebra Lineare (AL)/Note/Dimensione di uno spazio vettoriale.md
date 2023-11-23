---
type: nota
course: Algebra Lineare
topic: 
tags: AL ToReview
---

Prev: [[Algebra Lineare (AL)]]

# Dimensione di uno spazio vettoriale
---
la _dimensione_ di uno [[Spazio Vettoriale|spazio vettoriale]] $V$ indicato con $\dim(V)$ è il la [[Cardinalità di un insieme|cadinalita]] della sua [[Base di uno spazio vettoriale|base]], se lo spazio non ha una base allora la sua dimensione è $\infty$

> [!example]
> - $\dim(\mathbb{K}^n)=n$
> - $\dim(\mathbb{K}_n[x]) =n+1$ (spazio dei [[Polinomi|polinomi]])
> - $\dim(M(m,n,\mathbb{K})) =n \times m$
> - $\dim(V) =\infty$  se $V$ _non ha base_


### Teorema
Due basi dello stesso spazio vettoriale $V$ hanno lo stesso numero di elementi $n$

>[!note]
> questo è il motivo per cui possiamo dire che  $V$  ha un unica dimensione

---
### Teorema
Sia $V$ uno spazio vettoriale e $U \subset V$ un [[Sottospazio Vettoriale]]. Vale $0 ≤ dim (U) ≤ dim (V)$. Inoltre:

- $dim (U) = 0 \iff U =\{0\}$
- $dim (U) = dim (V) \iff U =V$


## lemmi interessanti:
_Sia_ $V$ uno [[Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$. Supponiamo di avere:
- dei vettori $v_1, \dots, v_n \in V$ che generano $V$
- dei vettori $w_1,\dots, w_n \in V$ indipendenti
_Allora_ anche i vettori  $w_1, \dots , w_n$  generano $V$

