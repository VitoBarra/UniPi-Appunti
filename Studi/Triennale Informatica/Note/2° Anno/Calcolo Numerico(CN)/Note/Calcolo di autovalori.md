---
Subject: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Calcolo di autovalori
---

### Metodo delle potenze
è un metodo per calcolare un autovalore di una matrice

- Assumiamo che la matrice $A$ sia [[Matrici Diagonalizzabili|diagonalizzabile]]
	- $X^{-1}AX =D$ dalla definizione di diagonalizzabile  la riscriviamo come 
	- $AX =XD$ è quindi abbiamo che il l uguaglianza per righe come 
		- ![[Pasted image 20230511180931.png]]
	- assumiamo inoltre che l [[Autovettori e Autovalori|autovalore]] di modulo massimo sia unico
		- $|\lambda_{1}| > |\lambda_{2}| \geq |\lambda_{3}|\geq  \dots \geq|\lambda_{n}|$
		- il modulo è essenziale siccome potrei dover confrontare dei [[Insieme dei Numeri complessi|numeri complessi]] e numeri reali.
	
il metodo delle potenze cerca una sequenza di $k$ passi  
$$\begin{cases}
v^{(0)} \in \mathbb{R}^n \\
v^{(k+1)} = Av^{(k)}
\end{cases}$$
utilizzare questa metodo porta la [[Complessita|complessità]] del algoritmo a $O(k\cdot nnz(A))$ dove $nnz(A)$ sono i numeri di elementi non $0$ di $A$. questo si implementa sfruttando delle [[Strutture Dati|strutture dati]] per memorizzare la _matrice sparsa_. senza questo algoritmo il procedimento normale sarebbe
$$\begin{array}{}
v^{(1)} &=& Av^{(0)} \\
v^{(2)} &=& Av^{(1)} &=&A^{2}v^{(1)}  \\
v^{(k+1)} &=&A^{k+1}v^{(0)}
\end{array} $$
calcolare in questo modo ci porta la _complessità_ a $O(kn^{3})$ (per la moltiplicazione tra matrici eseguita $k$ volte $+ n^2$ per la somma del vettore ma si _ignora_) e non prossimo sfruttare la sparsità della matrice siccome questa si può riempire man mano che si moltiplicano. 

### Teorema 
sotto le ipotesi del _Metodo delle potenze_ questo restituisce un $v^{(k)}$ punto nella direzione di $x^{(1)}$ individua cioè l [[Autospazio|autospazio]]
##### Dimostrazione
per comodità si cambia la [[Base di uno spazio vettoriale|base]]  del vettore $v^{(0)}$
- $\exists y \in \mathbb{C}^{n,}\ \ \ y = \begin{bmatrix} \uppsi{i} \\ \uppsi_{2} \\  \vdots \\ \uppsi{n}\end{bmatrix}$
con $X$ la _base del autospazio_ allora possiamo scrivere
$$\begin{array}{}
v^{(0)} = Xy = \uppsi_{1}x^{(1)}+\uppsi_{2}x^{(2)}+\dots +\uppsi_{n}x^{(n)} \\
\end{array}$$ 
e da qui possiamo calcolare il prossimo vettore come.
$$
\begin{array}{}
v^{(1)} &=&Av^{(0)} &=& AXy \\ \\
&&&& A(\uppsi_{1}x^{(1)}+\uppsi_{2}x^{(2)}+\dots+\uppsi_{n}x^{(n)} )  \\
&&&& \uppsi_{1}Ax^{(1)}+\uppsi_{2}Ax^{(2)}+\dots+\uppsi_{n}Ax^{(n)} \\
&&&& \uppsi_{1}\lambda_{1}x^{(1)}+\uppsi_{2}\lambda_{2}x^{(2)}+\dots+\uppsi_{n}\lambda_{n}x^{(n)}
\end{array}
$$
e il fatto che sia diagonalizzabile mi permette di $AX=XD \implies$
$$v^{(1)} = Av^{(0)} = AXy = XDy$$
e il secondo passo
$$v^{(2)} = Av^{(1)} = AXDy= XD \cdot Dy=XD^{2}y$$
e da qui possiamo intuire che 
$$
\begin{array}{}
v^{(k)} & = & XD^{k}y & =  \\
 &=&\uppsi_{1}\lambda_{1}^{k}x^{(1)}+\uppsi_{2}\lambda_{2}^{k}x^{(2)}+\dots+\uppsi_{n}\lambda_{n}^{k}x^{(n)}  & = \\
&=& \lambda_{1}^{k} 
\left( \uppsi_{1}  x^{(1)}+\uppsi_{2}\left(\cfrac{\lambda_{2}}{\lambda_{1}}\right)^{k}+\dots+\uppsi_{n}\left(\cfrac{\lambda_{n}}{\lambda_{n}}\right)^{k}x^{(1)} \right)
\end{array}
$$
siccome sappiamo che $|\lambda_{1}|$ è il più grande il modulo abbiamo che tutte le $\left|\cfrac{\lambda_{i}}{\lambda_{1}}\right| <1$ per $\forall i = 2 ,\dots, n$
e quindi 
$$v^{(k)} \rightarrow_{k\to \infty} \lambda_{1}^{k}\uppsi_{1}x^{(1)}$$
e da qui possiamo dire $v^{(k)}$ è nella direzione di $x^{(1)}$ 

_Problemi_
1.  $\uppsi_{1}$ potrebbe essere $0$ o andare verso $0$.
2. a seconda del valore di $|\lambda_1|$
	- $>1$, $\lambda_1^k$  _divergere_ il che può facilmente portare ad [[Aritmetica di Macchina|overflow]]
	- $<1$, $\lambda_1^k$ _converge_ a $0$
	- $=1$, $\lambda_1^k$ tutto ok
_variante 1_
divido per $\lambda_1$ ad ogni passo. 
![[Pasted image 20230511224559.png]]
in questo modo ottengo che 
$$v^{(k)} \rightarrow_{k\to \infty} \uppsi_{1}x^{(1)}$$
ma $\lambda_{1}$ non lo conosciamo. e quindi questa soluzione per quanto ideale è infattibile.
il problema e nella lunghezza del vettore che può crescere o diminuire molto quindi per risolvere il problema si _normalizza_ il vettore.
![[Pasted image 20230511224943.png]]
in questo modo riusciamo ad ottenere l _autovettore_
#### quoziente di reileigh
questo server per calcolare l _autovalore_ associato al vettore calcolato

$$\lim_{ k \to \infty } \frac{v^{(k)T}Av^{(k)}}{v^{(k)T}v^{(k)}} = \lambda_{1}$$

## Varianti
ci sono delle varianti per trovare alti _autovettori_.

#### autovettore minimo (variante di wiland)
il calcolo del autovettore minimo funziona solo nella condizione in cui 
-  $|\lambda_{1}| \geq |\lambda_{2}| \geq |\lambda_{3}|>  \dots \geq|\lambda_{n}|>0$
e sfrutto il fatto che gli _autovalori_ di $A^{-1}$ siano i reciprochi e quindi ho che
$\frac{1}{|\lambda_{1}|} > \frac{1}{|\lambda_{2}|} \geq \frac{1}{|\lambda_{3}|}>  \dots \geq \frac{1}{|\lambda_{n}|}>0$
da qui posso usare algoritmo di prima 
$$\begin{cases}
v^{(0)} \in \mathbb{R}^n \\
v^{(k+1)} = A^{-1}v^{(k)}
\end{cases}$$
ma siccome calcolare $A^{-1}$ può essere difficile si moltiplica per $A$ e va a si risolve il [[Sistemi lineari e lineari omogenei|sistema lineare]] ottenendo.
$$\begin{cases}
v^{(0)} \in \mathbb{R}^n \\
Av^{(k+1)} = v^{(k)}
\end{cases}$$
per ottimizzare si può anche fare la [[Fattorizzazione LU]] su $A$

#### autovettore in mezzo 
il calcolo del _autovettore_ di mezzo qualsiasi funziona solo nella condizione in cui 
-  $|\lambda_{1}| \leq \dots\leq|\lambda_{i+1}| < |\lambda_{i}|<|\lambda_{i-1}| \leq  \dots \leq|\lambda_{n}|$
faccio in modo che il $\lambda_{1}$ diventi l _autovalore_ di modulo minimo e si applica la variante per cercare il minimo.
si fa  calcolando 
![[Pasted image 20230511231344.png]]