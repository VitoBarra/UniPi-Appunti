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
e quindi conoscendo $\Phi(n)$ e si puo calcolare con il [[Metodo di esponenziazioni successive|Metodo di esponenziazioni successive]] o calcolando una fattorizzazione di $n=pq$ con $p$ e $q$ primi 


### Estensione della funzione di Euclide
la relazione $$ax \equiv 1 \mod b$$dove $x$ è il valore incognito tale che $x = a^{-1} \mod b$ 
è _equivalente_ alla relazione
$$ax =bz+1$$per un opportuno $z$.
da questa relazione alternativa sostituendo $y=-z$ e $MCD(a,b)=1$  e riordinando otteniamo 
 $$ax+by = mcd(a,b)$$
 e questa nuova espressione puo essere risolta tramite l[[Algoritmo di Euclide per calcolare mcd|algoritmo di euclide]] esteso per risolvere l equazioni in due variabili. 
```pseudo
	\begin{algorithm}
	\caption{Euclide esteso}
	\begin{algorithmic}
	\Function{ExtendedEuclid}{a,b}
		\If{$b=0$} \Return $\langle a,1,0\rangle$
		
		\State $\langle d',x',y'\rangle \leftarrow$ \Call{ExtendedEuclid}{$b,a\mod b$}
		\State $\langle d,x,y\rangle \leftarrow  \langle d',y',x'-\lfloor a/b\rfloor y'\rangle $
		\Return $\langle d,x, y\rangle$
		\EndIf
	\EndFunction
	\end{algorithmic}
	\end{algorithm} 
```
e il risultato di questa funzione è una tripla $\langle mcd(a,b),x,y \rangle$ dove $x,y$ solo le _soluzioni del equazione_. 
E quindi avremo l inverso $x$ calcolato direttamente
la [[Complessita|complessita]] di questo algoritmo è _logaritmo_ nei valori di $a$ e $b$ e polinomiale nella dimensione di $a$ e $b$.

