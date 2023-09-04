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
#### Lemma di Euclide
_siano_ $a$ e $b$  interi diversi da 0. 
_allora_ $MCD(a+b,b) = mcd(a,b)$
##### Dimostrazione 
_siano_ $m=MCD(a+b,b),   \mu = MCD(a,b)$ allora$$\begin{array}{}
	m  & = &  mcd(a,b)  & \implies &  m|(a+b)\\
	 &  & m|b  & \implies  &  m|a\\
	 &  & m|b  & \implies  &  m \leq \mu   
\end{array}
$$
	dove per $\mid$ si intende che _[[Divisibilità tra numeri|divide]]_ allo stesso modo 	$$
\begin{array}{}
	\mu  & = &  mcd(a,b)  & \implies &  \mu|a\\
	 &  & \mu|b  & \implies &  \mu |(a+b)\\
	 &  & \mu|b  & \implies &  \mu\leq m
\end{array}
 $$
	quindi $m = \mu$

#### Algoritmo
_siano_ $a,b$ due numeri interi
Si vuole trovare il [[Massimo comun divisore|MCD]] tra $a$ e $b$
_se_ $a \geq b > 0$ e poniamo $a= qb+r$  che posso farlo per il [[Teorema della divisione|Teorema della divisione]] dove $b>r\geq0$ 
_allora_ vale che
$$MCD(a,b)= MCD(r+qb,b)= MCD (r,b)=MCD(b,r)$$
l algoritmo si ferma quando  $r=0$. in questo modo ottimo un algoritmo ricorsivo per calcolare il _MCD_
```C
int MCD_euclid(int a, int b) 
{   
	if (b>a) return MCD_euclid(b, a) 
	// chiamata al massimo solo la prima volta 
	if (b == 0) return a; // mcd(a,0)=a
	else return MCD_euclid(b, a % b);
}
```

questo algoritmo ha [[Complessita|Complessita]] $O(\log a+b)$ che è polinomiale nella lunghezza della [[Rappresentazione di oggetti matematici con sequenze|Rappresentazione]]