
---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Rappresentazione di oggetti matematici con sequenze
---
_sia_ un [[Alfabeto]]  $\Gamma$ Con $|\Gamma| = n$ e $N$  il numero degli _oggetti da rappresentazione_

_sia_ $d(n,N)$ la lunghezza della stringa piu lunga per rappresentare un oggetto, ovvero quella massima in funzione dei parametri, questa porrebbe essere grande a piacere a seconda di come decidiamo di rappresentare gli oggetti 
- ad esempio con $n=1$ se per ogni oggetto usiamo due simboli abbiamo che $d(n,N)=2N$
	- $d(1,4)=|00\ 00\ 00\ 00|=2\cdot 4$
		
_sia_ $d(n,N)_{min}$ il minimo valore di $d(n,N)$ tra tutte le rappresentazioni possibili.

Più $d(n,N)$ si avvicina a $d(n,N)_{min}$ più il metodo di  rappresentazione è _efficiente_ rispetto ai parametri

solitamente vogliamo rappresentare un numero di oggetti _arbitrario_ e quindi possiamo _efficientare_ la rappresentazione  migliorando il _metodo di rappresentazione_ e lavorando sui simboli che abbiamo a disposizione ($n$)

### Alcune rappresentazioni
#### Rappresentazione unirai
Con $n=1$ e _canonicamente_ $\Gamma = \{0\}$ abbiamo una rappresentazione detta _unaria_. 

ogni oggetti da rappresentare da una stringa di $0$ e quindi il _miglior metodo_ possibile è $1=0,2=00,3=000, \dots,N=N0$ e di conseguenza $d(n,N)_{min} =N$.

> [!warning]
> questa è una rappresentazione estremamente _svantaggiosa_. 


#### Rappresentazione binaria
Con $n=2$ canonicamente $\Gamma = \{0,1\}$  abbiamo una  Rappresentazione detta _Binaria_

in questa rappresentazione le possibili sequenze di lunghezza $k$ sono le [[Combinatoria|disposizioni con ripetizioni]] in gruppi di $k$ di $0$ e $1$. La somma di tutte le possibili sequenze è $\sum^{k}_{i=0}2^{i}=2^{k+1}-1$ che togliendo la stringa vuota diventa $2^{k+1}-2$

e per rappresentare $N$ oggetti c è quindi bisogni che sia vero $2^{k+1}-2\geq N$ quindi che sia vero
$$k \geq \log_{2}(N+2)-1$$
e siccome $d(2,N)_{min}$ é il _minimo numero intero_ che soddisfa questa diseguaglianza abbiamo che vale che 
$$d(2,N)_{min}=\left \lceil log_2(N+2)-1 \right\rceil$$
da cui si ottiene che
$$\left \lceil log_2(N) \right\rceil -1 \leq d(2,N)_{min} \leq \left \lceil log_2(N) \right\rceil$$


#### Rappresentazione N-aria
con $n\geq 2$ canonicamente $\Gamma = \{0,1,\dots,n-1\}$  abbiamo una  Rappresentazione detta _n-aria_.

è una generalizzazione di quella _binaria_ e valgono gli stessi ragionamento per cui vale che 
$$\left \lceil log_n(N) \right\rceil -1 \leq d(n,N)_{min} \leq \left \lceil log_n(N) \right\rceil$$


### Classificazione
le rappresentazioni con $d(n,N) = \theta(\log_{n}(N))$ (nel ordine di $log_n(N)$)  si dicono _efficienti_ e si pongono in alternativa alla rappresentazione _unitaria_.

### Metodi di rappresentazione a lunghezza fissa
se si usano metodi di rappresentazioni  con dimensione della stringa sempre uguale abbiamo che $d(n,N)=\lceil \log_{n}(N)\rceil$ per _ogni oggetto_ da rappresentare e di conseguenza  sostituendo nella relazione precedente abbiamo che $$d(n,N)\leq d_{min}(n,M)+1$$
In pratica abbiamo una piccola penalità sul efficienza perché perdiamo tutte le varie combinazioni diverse dove mancano dei caratteri. Il vantaggio di questo lo vediamo nei casi in cui dobbiamo concatenare piu oggetti, caso comune, siccome avere la rappresentazione a lunghezza variabile avrebbe aggiunto la necessita di usare delle marche di separazione tra i vari oggetti, il che avrebbe aggiunto complessità. 
con la lunghezza fissa ci basta saltare gli $\lceil \log_{n}(N)\rceil$ caratteri per andare al prossimo oggetto.

 