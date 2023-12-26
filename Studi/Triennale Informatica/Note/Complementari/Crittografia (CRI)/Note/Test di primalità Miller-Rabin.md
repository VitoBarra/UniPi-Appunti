---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Test di primalità Miller-Rabin
---
Il _test di primalità di Miller e Rabin_ è un [[Algoritmi Randomizzati|Algoritmo randomizzato]] per stabilire se un numero è [[Numeri primi|primo]]

### Algoritmo 
_Sia_ $N$ un numero _dispari_ 
	(cosi non fosse questo ovviamente non sarebbe primo)
Poniamo $N-1=2^{w}z$ con $z$ dispari e $w$ è il piu grande esponente che si puo dare a $2$
_sia_ $y$ un intero arbitrario con $y \in [2,N-1]$.

_Se_ $N$ è _primo_ 
_allora_ sono veri entrambi i due  predicati
1. $MCD(N,y)=1$
2. $\begin{array}{}y^{z} \mod N = 1  & \text{ or }\\ \exists i, 0 \leq i < w.\ \ y^{2^{i}z} \mod N = -1\end{array}$

Non vale pero il contrario.
Se i due predicati sono veri si può dire solo che il numero $N$ è primo con una certa probabiliotà 

#### Lemma Miller e Rabin
_se_ $N$ è _non primo_ (composto) i numeri $y$ con $1< y < N$ che _soddisfano entrambi i predicati_ sono minori di $\cfrac{N}{4}$

questo significa che il _test di primalità_ ha meno di $\cfrac{1}{4}$ di [[Definizione di Probabilita|probabilità]] di dichiarare un numero _composto_ come [[Numeri primi|numero primo]]

#### Verifica Probabilistica
Utilizzando il _lemma_ possiamo costruire l algoritmo di _verifica_ per il [[Certificato di un algoritmo|certificato Probabilistico]] $y$ 
```pseudo
	\begin{algorithm}
	\caption{Verifica primalita}
	\begin{algorithmic}
	\Function{verifica}{N,y}
		\Return ($P_1 =$ true) and ($P_2=$ true)
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Questa funzione di _verifica_ è interessante solo se il suo tempo di esecuzione è polinomiale, ed infatti è cosi. 

Per trovare i valori $w$ e $z$ tali che $N-1=2^{w}z$ con $z$ dispari bisogna dividere $N-1$ per $2$ $O(\log N)$ volte
 
Per verificare il _primo predicato_ si utilizza l [[Algoritmo di Euclide per calcolare mcd|algoritmo di euclide]] che è _polinomiale_ nella rappresentazione
per verificare il _secondo predicato_ si utilizza l [[Algoritmo delle Quadrature successive o esponenziazione veloce|algoritmo delle esponenziazione successive]] per calcolare $y^{z} \mod N$ cosa a costo _polinomiale_ e poi si calcola in successione $y^{2z},\dots y^{2^{w-1}z}$ elevando al quadrato ogni volta il precedente valore questo rende l algoritmo ancora _polinomiale_

e questo ci porta a concludere che _$verifica(N,y)$_ è in totale _polinomiale_

#### Test di primalità
Ora per verificare che un numero $N$ sia primo si puo procedere con il seguente _test di Miller-Rabin_
```pseudo
	\begin{algorithm}
	\caption{Test-MR}
	\begin{algorithmic}
	\Function{Test-MR}{$N$}
	\For{$i\leftarrow 1$ \to $k$}
	\State $y =$ \Call{Rand}{1,N}
	\If{\Call{Verifica}{N,y}=false}
	\Return false
	\EndIf 
	\EndFor
	\Return true
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Se il risultato è $false$ abbiamo che il numero $N$ è sicuramente _non è primo_ 
Se il risultato è $true$ sappiamo che $N$ è [[Numeri primi|primo]] con una certa [[Definizione di Probabilita|probabilità]] e sapendo che $Verifica(N,y)$ dichiara come _primo_ un numero _non primo_ con una probabilità di $\cfrac{1}{4}$, _ripetendo il test_, che sono indipendenti, $k$ volte abbiamo che la probabilita che $N$  sia _effettivamente primo_ è  $1-\left(\cfrac{1}{4}\right)^{k}$

>[!warning]
>questo funziona a patto che le scelte delle $y$ sia [[Indipendenza Stocastica|indipendenti]] utilizzano quindi un [[Generatori di numeri Pseudo Casuali|generatore di numeri pseudo casuli]] _crittograficamente sicuro_

La [[Complessita|complessità]] di questo algoritmo è facile da calcolare, abbiamo che la complessità di $Verifica(N,y)$ è polinomiale $p(n)$ facciamo questa operazione $k$ volte, quindi abbiamo che la _complessità_ è $O(k\cdot p(n))$. ovvero Polinomiale se $k$ è costante [[Polinomi|polinomiale]]. 