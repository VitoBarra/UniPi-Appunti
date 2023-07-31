---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema di Eulero
---
## Funzione di Eulero
sia un  $n\in \mathbb{N}$ con $n>1$ si definisce la _funzione di euloero_ come 
$$\Phi(n) = |\mathcal{Z_{n}^{*}}|$$
ovvero il numero di _interi minori_ di $n$ e _coprimi_ con $n$
se $n$ è un numero primo avremo che $\Phi(n)= (n-1)$ 

### Teorema
_sia_ $n$ il prodotto tra due [[Numeri primi|numeri primi]] $n =p\times q$
vale $$\Phi(n) = (p-1)(q-1)$$

### Teorema di Eulero
_sia_ $n \in \mathbb{N}$ con $n>1$ 
_allora_ $\forall a \in \mathcal{Z}_n^*$ ovvero per ogni $a$ coprimo con $n$
si ha che 
$$a^{\Phi(n)}\equiv 1 \mod n$$
ovvero vale che $a^{\Phi(n)}$ è congruo con $1 \mod n$