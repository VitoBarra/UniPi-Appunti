---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Rango
---

### Definizione
sia A una matrice $m \times n$ a coefficienti in $K$con $A^i$ intendiamo una qualsiasi colonna di $A$ e $A^i$ è un vettore in $K^m$

$$
St = Span(A^1,\dots,A^n)\subset K^m
$$

$$
rk(A) = dim(St)
$$

il rango di una matrice $A$ indicato con  $rk(A)$ è la dimensione dello spazio generato dalla sue colonne indipendenti

> #### Osservazioni
>- il ragno è anche detto come il massimo numero di colonne indipendenti
>- il rango non cambia con le mosse di Gauss

### Corollari interessanti:

- il ragno il numero di pivot di una matrice ridotta a scalini
- Se $A$ è una matrice $m \times n$  allora $rk(A) ≤ min\{m, n\}$
- Una matrice  $m \times n\ \ \ A$   ha rango massimo se $rk(A) = min\{m,n\}$
- per ogni matrice $A$  vale $rk(A) =rk({}^t\! A)$
- una [Sottomatrice](obsidian://open?vault=UniPi-Appunti&file=Raccolta%20UniPi%20INF%2FNote%2F1%C2%B0%20Anno%2FAlgebra%20Lineare%20(AL)%2FMatrici%2FSottomatrici) $B$  di $A$ ha sempre $rk(B)≤rk(A)$

---

il rango può esser calcolato tramite il [[Determinante di una matrice]]

infatti se

- la matrice $A \in N(n)$ allora $det(A)\not= 0 \iff rk(A)=n$ quindi massimo
    - questa cosa si può usare per capire se $n$ vettori messi in una matrice quadrata sono una base di $K^n$
- la matrice $A \in N(m,n)$ allora il rango è il massimo ordine $k$ di un suo
[minore](obsidian://open?vault=UniPi-Appunti&file=Minori%20di%20una%20matrice)  $B$ con $det(B)\not= 0$
