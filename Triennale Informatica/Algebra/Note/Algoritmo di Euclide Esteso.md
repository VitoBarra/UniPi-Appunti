---
Course: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Algoritmo di Euclide Esteso
---
Quest [[Algoritmi]] è una versione _estesa_ del [[Algoritmo di Euclide per calcolare mcd|Algoritmo di Euclide]] che altre a calcolare il [[Massimo comun divisore|MCD]] calcola anche i _coefficienti_ del [[Identità di Bezout|identità di  Bezout]]

```pseudo
	\begin{algorithm}
	\caption{Euclide esteso}
	\begin{algorithmic}
	\Function{ExtendedEuclid}{a,b}
		\If{$b=0$} \Return $\langle a,1,0\rangle$
		\EndIf
		
		\State $\langle d',x',y'\rangle \leftarrow$ \Call{ExtendedEuclid}{$b,a\mod b$}
		\State $\langle d,x,y\rangle \leftarrow  \langle d',y',x'-\lfloor a/b\rfloor y'\rangle $
		\Return $\langle d,x, y\rangle$
	\EndFunction
	\end{algorithmic}
	\end{algorithm} 
```
e il risultato di questa funzione è una tripla $\langle mcd(a,b),x,y \rangle$ dove $x,y$ solo le _i coefficienti_ del [[Identità di Bezout|Identità di Bezout]]. 

la [[Complessita|complessita]] di questo algoritmo è _logaritmo_ nei valori di $a$ e $b$ e polinomiale nella dimensione di $a$ e $b$.


#### Algoritmo di Euclide Esteso
```C
int MCD_esteso (int a, int b, int *u, int *v) 
{ 
int d, x, y;
 if (b == 0){ *u = 1; *v = 0; return a; } 
 d = MCD_esteso (b, a % b,&x,&y); 
 *u = y;
 *v = x + y*(a/b); 
 printf ( ”%d,%d|%d,%d\n” ,b,a % b,*u,*v); // Only for illustration return d;
```