---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Teorema della divisione
---
Siano $a$ e $b$ interi non-negativi tale che $a > 0$. Allora, esistono interi $q ≥ 0$ e $0 \leq r < a.\  b = qa+r.$
- $q$ è il quoziente
- $r$ è il resto 
##### Dimostrazione

$$S = \{b-ax \mid x \text{ è un intero non-negativo e } b -ax \geq0\}$$
 Allora, $S$ non è vuoto poiché  $b − ax = b \geq 0$ se $x = 0$. Allora, per il [[Principio di buon ordinamento e induzione|Principio di buon ordinamento]] implica che $S$ ha un elemento minimo $r$.
1. Per costruzione del ipotesi possiamo ricavare  $r = b − qa$ per qualche $q \geq 0$.
2. Dobbiamo dimostrare che $0 \leq r < a$.
	1. Supponiamo che $r \geq a$. Allora, $r −a=b−qa−a\geq0$ che contraddice la proprieà di minimalità di $r$. Quindi,
 $$b= qa + r,\ \ \ \ \ \ 0 \le r <a $$

#### univocità
sia $a$ e $b$ interi non negativi tale che $a > 0$  e sia $b= qa +r$ a dove $q \geq 0$ e $0 \leq r <a$. allora la coppia $(q,r)$ è unica

##### Dimostrazione
supponiamo che $(q’,r’)$ sia un altra coppia di interi tasche che $b= q’a+r’$ dove $q’\geq 0$ e $0 \leq r’ <a$ . si supponga che $r\geq r’$ allora
$$0=b-b=a(q-q’)+(r-r’)$$
e quindi $-a(q-q’)=(r-r’) \geq 0$, pero $0<r’<r<a$. dunque 
$$q’-q =(r-r’)/a, \ \ \ \ \ \ 0 \leq(r-r’)/a <1$$
- _notare_ lo sviluppo del meno nella parantesi
e quindi 
$$0 \leq q’-q <1$$
poichè $q’-q$ è un numero intererò ed è schiacciato tra 0 e 1, si deduce che $q’-q=0$ ovvero $q’ = q$. quindi espandendo $r$
$$r’=b-q’a=b-qa=r$$
si dimostra cosi che le quantità sono uguali 