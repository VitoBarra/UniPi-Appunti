---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Calcolare l inverso di un numero in algebra modulare
---
per _calcolare_ l inverso di $a \mod n$ abbiamo i seguenti metodi 

### Con la Funzione di Eulero
per ogni $a\in \mathcal{Z}_{n}^{*}$ ovvero $a$ nel [[Insieme dei coprimi|Insieme dei coprimi]] di $n$
vale che per il [[Teorema di Eulero|teorema di Eulero]] abbiamo 
$$a^{\Phi(n)}  \equiv 1 \mod n\implies a \times a^{\Phi(n)-1} \equiv \mod n$$
e per definizione di [[Inverso di un numero in algebra modulare|inverso]] abbiamo che 
$$a\times a^{-1} \equiv 1 \mod n$$
e questi due fatti insieme fanno concludere che 
$$a^{ -1}=a^{\Phi(n)-1} \mod n$$
e quindi conoscendo $\Phi(n)$ e si puo calcolare con il [[Algoritmo delle Quadrature successive o esponenziazione veloce|Algoritmo delle Quadrature successive o esponenziazione veloce]] o calcolando una fattorizzazione di $n=pq$ con $p$ e $q$ primi 


### Usare la funzione  estesa di Euclide
la relazione $$ax \equiv 1 \mod b$$dove $x$ è il valore incognito tale che $x = a^{-1} \mod b$ 
è _equivalente_ alla relazione
$$ax =bz+1$$per un opportuno $z$.
da questa relazione alternativa sostituendo $y=-z$ e $MCD(a,b)=1$  e riordinando otteniamo 
 $$mcd(a,b)=ax+by $$
 e questa nuova espressione è l [[Identità di Bezout|Identità di Bezout]] e può essere risolta tramite l [[Algoritmo di Euclide Esteso]] e quindi avremo che $x$ sarà calcolato direttamente come uno dei risultati del algoritmo
 