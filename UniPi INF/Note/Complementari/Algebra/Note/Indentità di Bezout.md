---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Indentità di Bezout
---
_siano_ $a,b \in \mathbb{N}$
_Se_ $(a,b) \not= (0,0)$ e  $d = MCD(a,b)$  ([[Massimo comun divisore]])
_allora_ esistono due interi $u$ e $v$ tale che $d=au+bv$

### Trovare u e v
per trovare gli interi $u$ e $v$ tali che $m = MCD(a,b) = au+bv$
$$au+bv= m \implies m= (qb+r)u + bv = ru + b(v+qu)$$
Quindi, ricorda che questo processo di calcolo di $mcd(a,b)$ per riduzione termina con $MCD(m,0)$. A quel punto, abbiamo $m = m(1) + 0(0)$. Pertanto, possiamo calcolare gli interi $u$ e $v$ utilizzando il seguente algoritmo esteso di Euclide:
$$
\begin{equation}\begin{split}
MCD(a,b\mid u,v) =
MCD(qb+r,b \mid u,v) =
\\ MCD(r,b \mid u,b+qu)=
\\ MCD(b,r \mid v,+qu,u) =
\\ \dots =
\\ MCD(m,0,\ell_1(u,b)\mid\ell_2(u,v))  \ \ \ \
\end{split}\end{equation}
$$
dove $\ell_1(u,b)=1, \ell_2(u,v)=0$ è un sistema di lineare $2 \times 2$ di equazioni in $u$ e $v$


#### algoritmo in codice
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

### Lemma di euclide 
Un intero$p > 1$ è un numero primo se e solo se $p|ab$ implica che $p | a$ o $p | b$, per tutti gli interi $a$ e $b$. 
##### dimostrazione
Supponiamo che $p$ sia un primo. notiamo $MCD(a,p) \not= 1 \implies p|a$
Allo stesso modo, se $MCD(b,p) \not= 1 \implies p|b$. Quindi, dopo aver cambiato $a$ e $b$ se necessario, possiamo supporre che $MCD(a,p) = 1$. 
Per il lemma di Bezout, esistono interi $u$, $v$ tali che $pu +av = 1$. Dunque
$$ b =b(pu+av) = pbu+abv $$Poich´e $p | p$ e $p | ab$ (per ipotesi), $p | pbu + abv = b$, come desiderato.
Viceversa, se $p$ non è primo allora esistono due interi $a$ e $b$ maggiori di uno tale che $p =ab$. In particolare, $p = ab$ e $a > 1 \implies b < p$. Quindi $p \nmid b$ ovvero p non [[Divisibilità tra numeri|divide]] b. Allo stesso modo, $p \nmid a$

