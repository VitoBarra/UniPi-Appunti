---
Subject: "[[Algebra (ALG)]]"
topic: nota
tags:
  - ALG
---
# Calcolare l inverso di un numero in algebra modulare
---
per _calcolare_ l [[Inverso di un numero in algebra modulare|inverso]] di $a\mod n$ abbiamo i seguenti metodi 

### Con la Funzione di Eulero
per ogni $a\in \mathcal{Z}_{n}^{*}$ ovvero $a$ nel [[Insieme dei coprimi|Insieme dei coprimi]] di $n$
vale che per il [[Teorema di Eulero|teorema di Eulero]] abbiamo 
$$a^{\Phi(n)}  \equiv 1 \mod n\implies a \times a^{\Phi(n)-1} \equiv \mod n$$
e per definizione di [[Inverso di un numero in algebra modulare|inverso]] abbiamo che 
$$a\times a^{-1} \equiv 1 \mod n$$
e questi due fatti insieme fanno concludere che 
$$a^{ -1}=a^{\Phi(n)-1} \mod n$$
e quindi conoscendo $\Phi(n)$ e si puo calcolare con il [[Algoritmo delle Quadrature successive o esponenziazione veloce|Algoritmo delle Quadrature successive o esponenziazione veloce]] o calcolando direttamente come $\Phi(n)=(p-1)(q-1)$ se si conosce la [[Teorema fondamentale del aritmetica|fattorizzazione]] di $n=pq$ con $p$ e $q$ [[Numeri primi|primi]] 


### Usare la funzione  estesa di Euclide
la relazione $$ax \equiv 1 \mod b$$dove $x$ è il valore incognito tale che $x = a^{-1} \mod b$  ovvero è l [[Inverso di un numero in algebra modulare|inverso]] di $a$ che esiste unico solo se $MCD(a,b)=1$
è _equivalente_ alla relazione
$$ax =bz+1$$per un opportuno $z$.
da questa relazione sostituendo $y=-z$ e $MCD(a,b)=1$  e riordinando otteniamo $$MCD(a,b)=ax+by $$
 e questa nuova espressione è l [[Identità di Bezout|Identità di Bezout]] e può essere risolta tramite l [[Algoritmo di Euclide Esteso]] e quindi avremo che $x$ sarà calcolato direttamente come uno dei risultati del algoritmo dove l inverso sarà
 $x$ se $a>b$
 $y$ se $b>a$
 