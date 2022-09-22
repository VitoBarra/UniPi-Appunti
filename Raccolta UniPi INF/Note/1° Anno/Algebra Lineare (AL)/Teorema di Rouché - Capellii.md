---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Teorema di Rouché - Capellii
---
dato un sistema lineare qualsiasi, trovando $A$ la matrice associata al sistema lineare e $b$ il vettore colonna dei termini noti. il sistema ha soluzione se:

$$
rk(A|b) = rk(A)
$$

lo spazio delle soluzioni $S \subset K^n$ è un sottospazio affine di dimensione $n − rk(A)$

### Corollario:

le soluzioni di un sistema lineare sono

- $0$ se $rk(A|b) > rk(A)$
- $1$ se $rk(A| b) = rk(A) = n$
- $\infty$ se $rk(A|b) = rk(A) < n$

dove è $dim(K^n) =n$

ne deduciamo che in un sistema lineare omogeneo esistono sempre soluzioni siccome $b=0$ e quindi  $rk(A|b) = rk(A)$ sempre
