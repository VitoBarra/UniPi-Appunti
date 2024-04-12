---
Subject: Algebra Lineare
topic: nota
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Teorema di Rouché - Capellii
---
dato un [[Soluzioni di un sistema lineare|sistema di equazioni lineari]]  qualsiasi, trovando $A$ la matrice _associata al sistema_ lineare e dato il vettore colonna dei termini noti $b$ . il sistema ha soluzione se:

$$
rk(A|b) = rk(A)
$$

lo spazio delle [[Soluzioni di un sistema lineare|soluzioni]] $\mathcal{S} \subset K^n$ è un [[Sottospazii affini| sottospazio affine]] di dimensione $n − rk(A)$

#### Corollario
le soluzioni di un sistema lineare sono
- $0$ se $rk(A|b) > rk(A)$ [[Rango|^]]
- $1$ se $rk(A| b) = rk(A) = n$
- $\infty$ se $rk(A|b) = rk(A) < n$

dove è $dim(\mathbb{K}^n) =n$

ne deduciamo che in un [[Sistemi lineari e lineari omogenei|sistema lineare omogeneo]] esistono sempre soluzioni siccome $b=0$ e quindi  $rk(A|b) = rk(A)$ sempre
