---
Subject: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---

# Teorema di Rouché - Capelli
---
dato un [[Soluzioni di un sistema lineare|sistema di equazioni lineari]]  qualsiasi, trovando $A$ la matrice _associata al sistema_ lineare e dato il vettore colonna dei termini noti $b$ . il sistema ha soluzione se$$
rk(A\mid b) = rk(A)
$$
lo spazio delle [[Soluzioni di un sistema lineare|soluzioni]] $\mathcal{S} \subset \mathbb{K}^n$ è un [[Sottospazi affini|sottospazio affine]] di dimensione $n − rk(A)$

#### Corollario
le soluzioni di un sistema lineare dipendono dal [[Rango|rango]] infatti
- $0$ se $rk(A\mid b) > rk(A)$ 
- $1$ se $rk(A\mid b) = rk(A) = n$
- $\infty$ se $rk(A\mid b) = rk(A) < n$

dove è $dim(\mathbb{K}^n) =n$

ne deduciamo che in un [[Sistemi lineari e lineari omogenei|sistema lineare omogeneo]] esiste sempre una soluzione questo  siccome con $b=0$ vale sempre che $rk(A\mid b) = rk(A)$






