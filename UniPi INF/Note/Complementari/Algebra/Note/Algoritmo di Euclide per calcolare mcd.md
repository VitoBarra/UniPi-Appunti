---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Algoritmo di Euclide per calcolare mcd
---
è un algoritmo per calcolare il [[Massimo comun divisore|Massimo comun divisore]]

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