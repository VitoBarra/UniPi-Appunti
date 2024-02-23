---
Subject: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema fondamentale del aritmetica
---
Ogni _numero_ $n>1$ o è un  [[Numeri primi|numero primo]] o si può esprimere come prodotto di _[[Numeri primi|numeri primi]]_. 
Tale rappresentazione è _unica_ ignorando l ordine dei fattori.

##### Dimostrazione di esistenza
_Sia_ $P(n)$ la proposizione che l intero $n>1$ è un numero primo oppure può essere espresso come prodotto di numeri primi. allora $P(2)$ è vera. Supponiamo che $P(2)…P(n)$ siano vere. allora anche $P(n+1)$ è vera.
- Se $n+1$ è primo, non c p nulla da dimostrare 
- Se $n+1$ non è primo allora $n+1=ab$ dove $1 <a,b < n+1$ per ipotesi di induzione $a$ e $b$ sono o primi o prodotti di primi


### Lemma di Euclide 
un intero $p>1$ è un un [[Numeri primi|numero primo]] se e solo se $$p\mid ab \implies p \mid a \lor p \mid b \ \ \ \forall a,b \in \mathbb{N}$$
dove per $|$ si intende _[[Divisibilità tra numeri|divide]]_
##### Dimostrazione di unicita 
_Sia_ $S$ l insieme degli interi $>1$ per i quali la parte di unicità del teorema fondamentale dell aritmetica fallisce. Se $S$ non è vuoto, ha un elemento più piccolo $n$. Siano 
$$n = p_1,\dots,p_k, \ \ \ \ \ \ n = q_1, \dots,q_\ell$$
due distinte fattorizzazione prime di $n$. allora poiché $p_1\mid n$, $p_1$ deve dividere qualche $q_j$ per il lemma di Euclide. Dopo aver riordinato i fattori $q_1,\dots,q_\ell$, possiamo assumere che $j=1$. Poiché $p_1$ e $q_1$ sono entrambi primi, ne consegue che $p_1=q_1$ Allora $$m=p_2\dots p_k= q_2 \dots q_\ell$$
ha anche due fattorizzazione distinte, ma $m < n$ contraddice la minimalista di $n$