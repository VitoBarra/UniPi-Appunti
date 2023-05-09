---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Massimo comun divisore
---
#### Definizione
Sia $S$ un sottoinsieme dei numeri reali $\mathbb{R}$ allora $m \in \mathbb{R}$ è una elemento massimo di $S$ se 
1. $m \in S$
2. $s \in S \implies s \leq m$
in generale pero non esiste sempre un elemento massimo un sotto insieme aperto di $\mathbb{R}$ non ha un  _massimo_


#### Lemma 1
Sia $S \subseteq \mathbb{R}$ . Se $S$ ha un elemento massimo $m$, allora $S$ ha un unico elemento massimo
##### Dimostrazione
Siano $m$ e $m’$ elementi massimi di $S$ . Allora $m \leq m’$ perché $m’$ è massimo. allo stesso modo $m’\leq m$ perché $m$ è massimo. Cosi $m=m’$

#### Lemma 2 
Sia $S \subseteq \mathbb{R}$ un insieme finito e non vuote. Allora, $S$ ha un elemento massimo
##### Dimostrazione
Sia $P(n)$ la proposizione che se $S$ ha $n \geq 1$ elemento allora $S$ ha un elemento massimo. 
- la Preposizione $P(1)$ è vera.
- Supponiamo che $P(n)$ sia vera e $S$ un insieme con $n+1$ elementi.
- Scegli un elemento $s \in S$ e sia $S’ = S - \{s\}$. quindi $S’=S-\{s\}$ ha $n\geq 1$ elementi. Poiché $P(n)$ è vera, ne consegue che $S’$ ha un elemento massimo detto $s’$.
- il massimo $m= max(s,s’)$  è un elemento massimo di $s$ in particolare $P(n+1)$ è vera

#### Definizione
dati $n$ un intero si definisce $$D(n) =\{d \in \mathbb{Z}|\ \ \  d\mid n\}$$
nota che $D(0) = \mathbb{Z}$


#### Preposizione
Sia $n$ un intero diverso da zero. Allora $D(n) \subseteq \{- |n|,\dots,|n|\}$. in particolare, $D(n)$ è un insieme finito
##### Dimostrazione
$m \in D(n) \implies \exists k \in \mathbb{Z} \ | \ n = km$. in particolare $k \not=0$ e $m \not=0$ perche $n \not= 0$ allora
$$|n|=|km|=|k||m| \implies |k|,|m| \leq |n|$$

#### Definizione
Siano $a$ e $b$ interi tale che $(a,b) \not=(0,0)$ il massimo comune divisione di $a$ e $b$, scritto $med(a,b)$ è il massimo elemento dell insieme $D(a)\cap D(b)$

> [!note] note
> se $a =0, b\not=0 \implies mcd(a,b)=b$

##### Algoritmo di calcolo mcd
```C++
int mcd(int a, int b) // Assumes a, b>0
{
	int k, m;
	for(m=1, k=1; k<a+1; k++) // a % k = remainder of a/k 
		if (((a % k)==0)) && ((b % k)==0))
			m=k;
	return m;
}
```

> [!note]
> una altro metodo molto lento è fattorizzare $a$ e $b$

### Algoritmo di Euclide
siano $a$ e $b$  interi diversi da 0. allora $mcd(a+b,b) = mcd(a,b)$
##### Dimostrazione 
siamo $m=mcd(a+b,b)  \mu = mcd(a,b)$ allora
	$$\begin{matrix}
	m = mcd(a,b) \implies m|(a+b)\\
	m|b \implies m|a\\
	m|b \implies m \leq \mu   
	\end{matrix} $$
	allo stesso modo 
	$$\begin{matrix}
	\mu = mcd(a,b) \implies \mu|a\\
	\mu|b \implies \mu (a+b)\\
	\mu|b \implies \leq m
	\end{matrix} $$
	quindi $m = \mu$

#### codice Algoritmo
supponiamo $a \geq b > 0$ e scriviamo $a= qb+r$ dove $0 \leq r <b$ allora 
$$mcd(a,b)= mcd(r+qb,b)= mcd (r,b)=mcd(b,r)$$
l algoritmo si ferma quando  $r=0$. in questo modo ottimo un algoritmo ricorsivo per calcolare il _mcd_
```C
int mcd_euclid(int a, int b) 
{   
	if (b == 0) // mcd(a,0)=a
	return a; 
	if (b>a) mcd(b,a) // Switch roles of a and b
	return mcd(b, a % b);
}
```