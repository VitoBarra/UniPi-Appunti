---
Subject: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Massimo comun divisore
---
#### Definizione
Sia $S$ un [[Insiemi Matematici|sottoinsieme]] dei numeri reali $\mathbb{R}$ allora $m \in \mathbb{R}$ è una elemento massimo di $S$ se 
1. $m \in S$
2. $s \in S \implies s \leq m$
in generale pero non esiste sempre un elemento massimo un sotto insieme aperto di $\mathbb{R}$ non ha un  _massimo_


#### Lemma 1
Sia $S \subseteq \mathbb{R}$ . Se $S$ ha un elemento massimo $m$, allora $S$ ha un unico elemento massimo
##### Dimostrazione
Siano $m$ e $m’$ elementi massimi di $S$ . Allora $m \leq m’$ perché $m’$ è massimo. allo stesso modo $m’\leq m$ perché $m$ è massimo. Cosi $m=m’$

#### Lemma 2 
Sia $S \subseteq \mathbb{R}$ un insieme finito e non vuoto. Allora, $S$ ha un elemento massimo
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
$m \in D(n) \implies \exists k \in \mathbb{Z} \ | \ n = km$. in particolare $k \not=0$ e $m \not=0$ perché $n \not= 0$ allora
$$|n|=|km|=|k||m| \implies |k|,|m| \leq |n|$$

#### Definizione
Siano $a$ e $b$ interi tale che $(a,b) \not=(0,0)$ il _massimo comune divisione_ di $a$ e $b$, scritto $mcd(a,b)$ è il massimo elemento del insieme $D(a)\cap D(b)$

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
> mentre uno piu veloce è l [[Algoritmo di Euclide per calcolare mcd|Algoritmo di Euclide per calcolare mcd]]
