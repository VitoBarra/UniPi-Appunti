---
Course: "[[Calcolo Numerico(CN)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CN
---

# Precisione di macchina
---
la __precisione di macchina__ $u$ e' una caratteristica della [[Aritmetica di Macchina|aritmetica di macchina]].
E' una quantità che da un upper Bound al errore commesso dalla rappresenta in [[Insieme dei numeri di macchina|numeri di macchina]] di numeri reali.

 la __precisione di macchina__ ha le seguenti proprietà
- è _indipendente_ dalla grandezza del numero che si vuole rappresentare
- è una _caratteristica_ del [[Aritmetica di Macchina|aritmetica di macchina]] ovvero dipende dal 
	- Insieme dei [[Insieme dei numeri di macchina|numeri rappresentabili]] 
	- Tecnica di approssimazione 
		- con $\beta$ la base e  $t$ il numero di cifre decimali a disposizione si ha che 
			- Troncamento: $u=\beta^{1-t}$  
			- Arrotondamento: $u=\cfrac{1}{2}\beta^{1-t}$  



### Definizioni
- $trn(x) = \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite _troncamento_ della parte decimale non rappresentabili  
- $arr(x)= \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite l _arrotondamento_ al numero di macchina più vicino 

#### Teorema errore assoluto
_sia_ un   $x \in \mathbb{R}$ che si vuole rappresentare in aritmetica di macchina
_se_  $\omega \leq |x|\leq \Omega$ over non ci sono casi di _overflow_ o _underflow_ 
_vale che_
 - $\mu_x=|trn(x)-x| < \beta^{p-t}$
 - $\mu_x=|arr(x)-x| \leq \frac{1}{2}\beta^{p-t}$

##### Dimostrazione
_sia_ $x \in \mathbb{R}$ il numero che voglio rappresentare in [[Insieme dei numeri di macchina|numeri di macchina]] abbiamo che 

per il caso $x \in \mathscr{F}(\beta,t,m,M)$ abbiamo che 
- $trn(x)=arr(x)=x$
- $trn(x)-x =0$
- $arr(x) -x =0$
per il caso $x \not \in \mathscr{F}(\beta,t,m,M)$  e $\omega \leq |x| \leq \Omega$ sia a che 
_sia_ $a = \beta^p\alpha$ un _numero di macchina_ qualsiasi e $b = \beta^p(\alpha + \beta^{-t})$  _numero di marchiana successore_ di $a$ abbiamo che $|b-a| = \beta^{p-t}$
e ci poniamo nel caso in cui  $a < x < b$  allora abbiamo che 
1. $\tilde x = trn(x) = a$ e possiamo quindi maggiorare l errore assoluto come$$\begin{array}{}
  \mu_x = |trn(x)-x|=|a-x|<|a-b| = \beta^{p-t} \\  \\
  \mu_x<\beta^{p-t}
  \end{array}
$$
2. $\tilde x = arr(x) = \begin{cases} a \text{ if } x < \cfrac{a+b}{2} \\ b \text{ if } x \geq \cfrac{a+b}{2}  \end{cases}$ e abbiamo quindi che
	$$\begin{array}{}
\mu_x = |arr(x)-x|\leq \cfrac{|a-b|}{2} = \cfrac{\beta^{p-t}}{2}  \\
\mu_x \leq \cfrac{\beta^{p-t}}{2}
\end{array} $$
	- posso fare questa maggiorazione siccome vale $a \leq x < b$  e l _arrotondamento_ porta al più vicino numero di macchina. la distanza tra $x$ e quel numero è sempre $\leq \cfrac{|a-b|}{2}$  l esatto numero rappresenta l equidistanza tra  $a,b$

#### Teorema errore relativo
_sia_ $x \in \mathbb{R}$ 
_se_  $\omega \leq |x|\leq \Omega$ ovvero non ci sono casi di _overflow_ o _underflow_ 
_allora_ vale
$$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} \leq u = 
\begin{cases}
\beta^{1-t} &\text{if} &\tilde  x = trn(x)\\
\frac{1}{2}\beta^{1-t} & \text{if}& \tilde x = arr(x)
\end{cases}
$$
la quantità $u$ è detta _precisione di macchina_ 
##### Dimostrazione
- Sappiamo che $x \geq \beta^{p-1}$
	- siccome $x=\beta^p(\sum^\infty_{i=1}d_{i}\beta^{-i})$ e $\beta^{p-1}= \beta^p(10\dots0)_t$
	- essenzialmente stiamo dicendo che $x$ è maggiore del valore con solo con stesso esponente ma con valore della mantissa minima
- _Troncamento_: $\tilde x = trn(x)$
	- Sappiamo che $|\tilde x-x| < \beta^{p-t}$ dal _teorema del errore assoluto_$$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} \leq \frac{\beta^{p-t}}{\beta^{p-1}}=\beta^{1-t}$$
- _Arrotondamento_: $\tilde x = arr(x)$
	- Sappiamo che $|\tilde x-x| \leq \frac{1}{2} \beta^{p-t}$ dal _teorema del errore assoluto_ $$|\epsilon_x|=\frac{|\tilde x-x|}{|x|} \leq \frac{\frac{1}{2}\beta^{p-t}}{\beta^{p-1}} = \frac{1}{2}\beta^{1-t}$$

##### Controllare qual è la precisione di macchina
 Per valutare la precisione di macchina possiamo determinare il piu piccolo numero di macchina maggiore di $1$. Detto infatti $x$ tale numero abbiamo che $x − 1 = |x−1| = \beta^{1−t}$ essendo $1 = \beta^1 \cdot \beta^{−1}$ rappresentato con esponente $p = 1$. Il seguente script MatLab fornisce il valore richiesto 
 ```mathlab
eps = 0.5
eps1 = eps+1
while(eps1>1)
	eps =0.5*eps
	eps1 = eps+1
end
eps = 2*eps
```

In sostanza, lo script funziona perché sfrutta le caratteristiche del sistema di numerazione floating-point utilizzato dal computer per calcolare la più piccola frazione rappresentabile. Il valore di eps calcolato dallo script rappresenta l'errore di rappresentazione minimo che può essere commesso durante i calcoli numerici sul computer.
