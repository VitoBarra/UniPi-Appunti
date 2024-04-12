---
Subject: "[[Fondamenti Del Informatica (FDI)]]"
Area: 
topic: 
SubTopic: 
tags:
  - FDI
---

# Combinatoria
---
#### Permutazioni
_sia_ $n$ un numero 
_allora_ il numero di modi in cui si possono ordinare gli elementi di $\{ 1,\dots,n \}$ è la formula $$n!$$
ovvero questo è il numero delle diverse permutazioni che si possono generare usando gli elementi del insieme. 

costruendo iterativamente la permutazione possiamo immaginare di dover riempire $n$ spazzi e per farlo al primo spazio abbiamo $n$ scelte al secondo $n-1$ e al terzo $n-2$ e cosi via, motivo per cui il [[Fattoriale|fattoriale]] descrive perfettamente questo numero.
##### Permutazione cona ripetizioni
le _permutazioni_ con ripetizioni, ovvero abbiamo un insieme dove alcuni elementi sono equivalenti è descritto dal numero   $$P^{n_{1},\dots,n_{n}}_{n}=\frac{n!}{n_{1}!,\dots,n_{n}!}$$
dove come prima stiamo effettuando delle _scelte_ ma va tenuto in considerazione il fatto di avere _piu elementi equivalenti_ che quindi non contano come scelte separate. Gli elementi ripetuti si possono contare e per torglieli dal conteggio finale si divide per il numero di modi _diversi_ che si ha di scegliere tra quei elementi _equivalenti_, questo spiega il [[Fattoriale|Fattoriale]]  
>[!tip]
>Ci si puo contare il numero di _anagrammi_ di una parola


#### Combinazioni
_siano_ $0 \leq k \leq n$ dei numeri naturali
_allora_ il numero di sottoinsiemi _NON ordinati_ di $\{ 1,\dots,n \}$ formati da $k$ elementi  è$$\begin{pmatrix}
n \\k
\end{pmatrix}=\frac{n!}{k!(n-k)!}$$
dove dividiamo per $k!$ per togliere dal conto tutti i vari possibili modi di _permutare_ gli elementi scelti

#### Disposizioni
_sia_  $A$ un [[Insiemi Matematici|insieme]] finito con $|A| = n$ e un intero $k ≤ n$
_allora_ una _disposizione_ degli elementi di $A$ è il numero di [[Insiemi Matematici|sottoinsiemi]] ordinati di $A$ di $k$ elementi ed è il numero $$\frac{n!}{(n-k)!}$$Questo numero coincide con il numero di _[[Applicazioni tra insiemi#Iniettiva|applicazioni iniettive]]_ da $\{ 1,\dots,k \}$ in $\{ 1,\dots,n \}$

lo si puo immaginare come una _sequenza ordinata_ di lunghezza $k$ $a_1, \dots , a_k$ dove esattamente $k$ elementi di $A$ appaiono esattamente una volta.


si puo esprimere una _disposizione_ con una _combinazione_ con la formula$$\begin{pmatrix}
n \\ k
\end{pmatrix} \cdot k! = \frac{n!}{(n-k)!}$$
ovvero si genera una sola combinazione degli elementi e poi li si _permuta_  

##### Disposizione con ripetizioni
_Siano_ $k$ ed $n$ due interi
_allora_ il numero di [[Applicazioni tra insiemi|applicazioni]] di $\{1,\dots,k\}$ a $\{ 1,\dots,n \}$ è $$n^{k}$$ovvero il numero di modi in cui possiamo _scrivere_ $n$caratteri in $k$ _spazzi_ senza nessun costrizione su quali e quanti caratteri usare.

