---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Test di primalità Miller-Rabin
---
il _test di primalità di Miller e Rabin_ è un [[Algoritmi Randomizzati|Algoritmo randomizzato]] per stabilita se un numero è [[Numeri primi|primo]]

### Algoritmo 
_Sia_ $N$ un numero _dispari_ cosi non fosse questo ovviamente non sarebbe primo.
poniamo $N-1=2^{w}z$ con $z$ dispari. $w$ è il piu grande esponente che si puo dare a $2$
_sia_ $y$ un intero arbitrario con $2 \leq y \leq N-1$.

_Se_ $N$ è primo devono essere veri i due predicati
1. $mcd(N,y)=1$
2. $\begin{array}{}y^{z} \mod N = 1  & \text{ or }\\ \exists i, 0 \leq i \leq w-1.\ \ y^{2^{i}z} \mod N = -1\end{array}$

#### Lemma Miller e Rabin
_se_ $N$ è composto i numeri $y$ con $2 \leq y \leq N-1$ che soddisfano entrambi i predicati sono minori di $\cfrac{N}{4}$.

questo significa che il _test di primalità_ ha meno di $1/4$ di probabilità di dichiarare un numero composto come [[Numeri primi|numero primo]]

#### Verifica Probabilistica
Utilizzando il _lemma_ possiamo costruire l algoritmo di _verifica_ per il [[Certificato di un algoritmo|certificato Probabilistico]] $y$ 
```pseudo
	\begin{algorithm}
	\caption{Verifica primalita}
	\begin{algorithmic}
	\Function{verifica}{N,y}
		\If{($P_1 =$ false) or ($P_2=$ false)}
		\Return 1
		\EndIf
		\Return 0
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Questa funzione di verifica è interessante solo se il suo tempo di esecuzione è polinomiale, ed infatti è cosi. 

Per trovare i valori $w$ e $z$ tali che $N-1=2^{w}z$ con $z$ dispari bisogna dividere $N-1$ per $O(\log N)$ (al massimo $\log N$ altrimenti meno volte).
 
Per verificare il _primo predicato_ si utilizza l [[Algoritmo di Euclide per calcolare mcd|algoritmo di euclide]] che è _polinomiale_
per verificare il _secondo predicato_ si utilizza l [[Algoritmo delle Quadrature successive o esponenziazione veloce|algoritmo delle esponenziazione successive]] per calcolare $y^{z} \mod N$ cosa a costo _polinomiale_ e poi si calcola in successione $y^{2z},\dots y^{2^{w-1}z}$ elevando al quadrato ogni volta il precedente valore questo rende l algoritmo ancora _polinomiale_

e questo ci porta a concludere che _$verifica(N,y)$_ è in totale _polinomiale_

#### Test di primalità
Ora per verificare che un numero $N$ sia primo si puo procedere con il seguente _metodo_ di Miller-Rabin
```pseudo
	\begin{algorithm}
	\caption{Test-MR}
	\begin{algorithmic}
	\Function{Test-MR}{$N$}
	\For{$i\leftarrow$ \to $k$}
	\State $y =$ \Call{Rand}{2,N-1}
	\If{\Call{Verifica}{N,y}$=1$}
	\Return 0
	\EndIf 
	\EndFor
	\Return 1 
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Se il risultato è $0$ di questo algoritmo è $0$ abbiamo che il numero $N$ sicuramente _non è primo_ ma se il risultato è 1 sappiamo che $N$ è [[Numeri primi|primo]] con probabilità $\left( 1-\left(\cfrac{1}{4}\right)^{k} \right)$ questo viene dal fatto che la [[Probabilità e variabili aleatorie|probabilità]] di scegliere un $y$ che soddisfa i predicati con $N$ non primo è  $\cfrac{1}{4}$ ed ad ogni nuova scelta di $y$  la probabilità di questa cosa si moltiplica, convertendo al evento a quello inverso abbiamo il valore indicato prima. 

>[!warning]
>questo funziona a patto che le scelte delle $y$ sia [[Indipendenza Stocastica|indipendenti]] utilizzano quindi un [[Generazione di numeri Pseudo Casuali|generatore di numeri pseudo casuli]] _crittograficamente sicuro_

La [[Complessita|complessità]] di questo algoritmo è facile da calcolare, abbiamo che la complessità di $verifica(N,y)$ è polinomiale $p(n)$ facciamo questa operazione $k$ volte, quindi abbiamo che la _complessità_ è $O(k\cdot p(n))$. ovvero Polinomiale se $k$ è costante [[Polinomi|polinomiale]]. 