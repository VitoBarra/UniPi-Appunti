---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Generatori di insieme di coprimi
---
_sia_ $n$ un numero e $\mathcal{Z}_{n}^{*}$ l [[Insieme dei coprimi|insieme dei numeri copirmi]] con $n$. 
un _generatore_ di $\mathcal{Z}_{n}^{*}$ è un numero $a\in\mathcal{Z}_{n}^{*}$ tale che l espressione 
$$a^{k} \mod n \ \ \ \ \ \  1\leq k\leq\Phi(n)$$
genera _tutti e soli_ gli elementi di $\mathcal{Z}_{n}^{*}$  senza ripetizioni.
essendo $\Phi(n)=|\mathcal{Z}_{n}^{*}|$ una sola ripetizione lascerebbe qualche elemento di $\mathcal{Z}_{n}^{*}$ fuori da quelli generati

per il [[Teorema di Eulero|teorema di eulero]] sappiamo che $a^{\Phi(n)} \mod n=1$ e per $k=\Phi(n)$ l espressione genera $1$ che è sempre elemento di  $\mathcal{Z}_{n}^{*}$. 
e deve quindi valere anche che $$a^{k} \not\equiv 1 \mod n \ \ \ \ \ 1 \leq k < \Phi(n)$$
### Teorema
per ogni $n$ [[Numeri primi|primo]], $\mathcal{Z}_{n}^{*}$ ammette almeno un generatore

### Teorema
per ogni $n$ [[Numeri primi|primo]], $\mathcal{Z}_{n}^{*}$ ammette esattamente $\Phi(n-1)$ generatori