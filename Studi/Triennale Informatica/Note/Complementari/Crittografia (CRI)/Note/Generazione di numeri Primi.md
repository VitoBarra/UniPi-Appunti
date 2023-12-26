---
type: nota
course: Crittografia
topic: 
tags:
  - CRI
Parent MOC: "[[Crittografia (CRI)]]"
---
# Generazione di numeri Primi
---
la generazione di numeri primi è un _problema importante_ per la crittografia siccome questi sono spesso utilizzati da i cifrari piu avanzati

Dal [[Distribuzione dei numeri primi|teorema dei numeri primi]] sappiamo che 
$$\lim_{ N \to \infty} numero \ di  \ primi \leq N = \frac{N}{\ln(N)} $$
e questi implica che se $N$ è grande cade un numero [[Numeri primi|primo]] in un [[Intorno|intorno]] di $N$ di lunghezza $\ln(N)$.

### Algoritmo di generazione di primi
Si puo scrivere il seguente _algoritmo_  che genera un numero [[Numeri primi|primo]]  di lunghezza di rappresentazione $n$  _bit_ questo è possibile utilizzando il [[Test di primalità Miller-Rabin|Test di primalità Miller-Rabin]] è una _sequenza_ $S$ di $n-2$ bit _generato casualmente_ da un [[Generatori di numeri Pseudo Casuali|generatore di numeri Pseudo Casuali]]

```pseudo
	\begin{algorithm}
	\caption{Generazione-primi}
	\begin{algorithmic}
	\Function{Primo}{n}
	\State $N \leftarrow 1S1$
	\While{\Call{Test-MR}{N}$=0$}
	\State $N \leftarrow N+2$ 
	\EndWhile 
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```

Siccome $\ln(N)$ é proporzionale alla _lunghezza_ $n$ della [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]] di $N$ abbiamo che il numero iterazione attese è polinomiale e l interno del ciclo è _polinomiale_ abbiamo che l intero algoritmo è _polinomiale_.

Notiamo che il primo $N$ che questo algoritmo trovata avrà al massimo $n+1$ bit, questo avviene siccome aumentare la rappresentazione di un  solo bit _significa raddoppiare il numero_ e tra $N$ e $2N$ cadono certamente molti numeri primi

