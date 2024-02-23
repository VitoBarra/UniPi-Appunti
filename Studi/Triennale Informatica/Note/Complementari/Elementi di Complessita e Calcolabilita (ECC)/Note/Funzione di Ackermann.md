---
Subject: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Funzione di Ackermann
---
la [[Funzioni|Funzione]] di ackermann è definita da
$$
\begin{align*}
A(0,0,y) & = y\\
A(0,x+1,y) &  = A(0,x,y)+1\\
A(1,0,y)  & = 0\\
A(z+2,0,y) & = 1\\
A(z+1,x+1,y) & = A(z,A(z+1,x,y),y)\\
\end{align*}
$$
i valori di queste espressioni ricorsive decrescono sempre quindi questa funzione è intuitivamente [[Calcolabilità|calcolabile]]

scritti in notazione più intuitiva questa funzione calcola
![[Pasted image 20221014174821.png]]
![[Pasted image 20221014174835.png]]