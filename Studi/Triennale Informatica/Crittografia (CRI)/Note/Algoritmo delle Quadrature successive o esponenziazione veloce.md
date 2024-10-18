---
Course: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Algoritmo delle Quadrature successive o esponenziazione veloce
---
è un _[[Algoritmi|algoritmo]]_ per il calcolo di$$x =y^{z} \mod s$$ con $y,z,s$ dello _stesso ordine di grandezza_

Si scompone $z$ in potenze dal $2$ e abbiamo quindi $z = 2^{w_{1}}+\dots+2^{w_{t}}$ con $w_{1}<\dots <w_{t}$ , Questa operazione è immediata se abbiamo la rappresentazione binaria di $z$ siccome ogni $w_{i}$ corrisponderà alla _posizione_ degli $1$ nella rappresentazione.

>[!example]-
se $z = 117_{10}=1110101_{2}$ avremo che $$\begin{array} {}
127 & = &  2^{0}+2^{2}+2^{4}+2^{5}+2^{6}\\ \\
127  & = &  1+4+16+32+64
\end{array}$$

Il calcolo diventa quindi
$x=y^{2^{w_{1}}+\dots+2^{w_{t}}}\mod s$ e questo puo essere calcolato come
$x=y^{2^{w_{1}}}\mod s+\dots+y^{2^{w_{t}}}\mod s$

Si calcolano le varie potenze di $y^{2^j}$ con $j = 1,2,\dots,w_{t}$ ottenendo ciascuna di esse come _quadrato della precedente_ riducendo cosi il numero di moltiplicazioni necessarie.
>[!example]
>$$y^{2}=y\times y \ \ ,\ \ y^{4}=y^{2}\times y^{2} \ \ , \ \ y^{8}=y^{4}\times y^{4}$$


Questo algoritmo porta il numero di operazioni moltiplicative a $\Theta(\log_{2}z)$, e per via della [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]] sappiamo che questo è Lineare nella _lunghezza della rappresentazione_. 