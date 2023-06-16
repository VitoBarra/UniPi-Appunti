
---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Rapresentazione di sequenze
---

Dato un [[Alfabeto]] di simboli $\Gamma$ Con $|\Gamma| = n$ e $N$  il numero degli oggetti da rappresentazione  $d(n,N)$ è il massimo numero di caratteri che servono  rappresentare un oggetto del insieme. il valore di $d(n,N)$ dipende dal metodo di rappresentazione scelto. $d(n,N)_{min}$ È il minimo numero tra tutte le rappresentazioni possibili.
Più $d(n,N)$ si avvicina a $d(n,N)_{min}$ più quella rappresentazione è efficiente 


## Esempi 
- Con $n=1$ e canonicamente $\Gamma = \{0\}$
	- è una rappresentazione detta unaria. ogni oggetti da rappresentare da una stringa di  $N$ zeri quindi $d(n,N)_{min} =N$ è quindi una rappresentazione svantaggiosa. 
- Con $n=2$ e canonicamente $\Gamma = \{0,1\}$
	- È una Rappresentazione detta Binaria e con questa con k caratteri si possono rappresentare 2^k oggetti che sono tutte le sue [[Combinatoria|Permutazioni]] e di k caratteri mantre utilizzando tutte le stringhe di lunghezza da 0 a k si possono rappresentare  $\sum_{i=0}^k 2^i= 2^{k+1}-1$ e togliendo la stringa vuota si rappresentano $2^{k+1}-2$  oggetti. Il che significa che per rappresentare $N$  serve   $2^{k+1}-2\geq$N  e quindi $k\geq log_2(N+2)-1$ .
	- $d(n,N)_{min}=\left \lceil log_2(N+2)-1 \right\rceil$
$$\left \lceil log_n(N) \right\rceil -1 \leq d(n,N)_{min} \leq \left \lceil log_n(N) \right\rceil$$
