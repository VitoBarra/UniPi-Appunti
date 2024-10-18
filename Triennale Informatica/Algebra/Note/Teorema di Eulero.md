---
Course: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema di Eulero
---
## Funzione di Eulero
_sia_ un  $n\in \mathbb{N}$ con $n>1$ si definisce la _funzione di euloro_ come 
$$\Phi(n) = |\mathcal{Z_{n}^{*}}|$$
ovvero il numero di _interi minori_ di $n$ e _[[Insieme dei coprimi|coprimi]]_ con $n$
_se_ $n$ è un numero primo avremo che $\Phi(n)= (n-1)$ 

### Teorema
_sia_ $n$ il prodotto tra due [[Numeri primi|numeri primi]] $n =p\times q$
vale $$\Phi(n) = (p-1)(q-1)$$

### Teorema di Eulero
_sia_ $n \in \mathbb{N}$ con $n>1$ 
_allora_ $\forall a \in \mathcal{Z}_n^*$ ovvero per ogni $a$ _[[Insieme dei coprimi|coprimo]]_ con $n$
si ha che 
$$a^{\Phi(n)}\equiv 1 \mod n$$
ovvero vale che $a^{\Phi(n)}$ è congruo con $1 \mod n$