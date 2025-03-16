---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---

# Determinante di una matrice
---
Il __determinate__ di una [[Matrici|matrice]] rappresenta il fattore per cui cambia l area di ciò che cè sul piano dopo che viene applicata la [[Matrici|matrice]]

Sia $A$ una matrice quadrata $n \times n$. 
_allora_ Il __determinante__ di $A$ è il numero

$$
det(A) = \sum_{\sigma \in S_{n}} sng(\sigma)
a_{1\sigma(1)}
\cdots
a_{n\sigma(n)}
$$

dove:
- $S_n$ = l insieme di $n!$ permutazioni
- $sgn(\sigma) = \pm1$ che indica il segno della permutazioni
- $\sigma(i) =$ una $i$-esima permutazione
- $a_{ij} =$  il $ij$-esimo elemento della matrice

se la matrice $A$ quadrata $n \times n$ è [[Matrici quadrate|triangolare (superiore o inferiore) o diagonale]]
allora il __determinante__ diventa $$
det(A)=a_{11}a_{22}\cdots a_{nn}
$$

## Mosse di Gauss

Sia una matrice $A \in M(n)$  applicando le [[Mosse di Gauss]] il determinante cambia nei seguenti modi

- Se $A'$ è ottenuta da $A$ scambiando due righe, $det(A') = − det(A)$
- Se $A'$ è ottenuta da $A$ moltiplicando una riga di $A$ per uno scalare $\lambda$, allora                $det(A') = \lambda det(A)$
- Se $A'$  è ottenuta da $A$ aggiungendo ad una riga il multiplo di un’altra riga, allora       $det(A') = det(A)$

---

Sia una matrice $A \in M(n)$ e supponiamo che la $i$esima colonna sia esprimibile come combinazione lineare di vettori colonna del tipo

$$
A^i = λ_1v_1 + · · · + λ_hv_h
$$

per qualche $v_j \in K^n$ e $λ_j ∈ K$. Sia $B_j$ la matrice ottenuta da $A$ sostituendo la colonna $A^i$
con $v_j$  per $j = 1,\dots,h$ vale$$
det(A)=\lambda_1 det(B_1)+\cdots+\lambda_h det(B_h)$$Corollario: siccome $det(A) =det({}^t\!A)$ questo vale anche per le righe