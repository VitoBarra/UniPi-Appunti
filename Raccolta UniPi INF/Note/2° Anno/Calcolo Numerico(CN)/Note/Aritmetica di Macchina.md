---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Aritmetica di Macchina
---
Rappresentare un numero  $x \in \mathbb{R} ,x   \not =0$  in un [[Insieme dei numeri di macchina|numeri di macchina]] significa approssimare $x$ con un numero $\tilde{x} \in \mathbb{F}(\beta,t,m,M)$ commettendo un [[Tipi di Errore nel calcolo numerico#Errori|errore relativo di rappresentazione]]
$$\epsilon_x=\frac{\tilde x-x}{x} = \frac{\mu_x}{x}$$
dove la quantità $$\mu_x = \tilde x -x$$ è detto [[Tipi di Errore nel calcolo numerico#Errori|errore assoluto di rappresentazione]]

>[!note] Errore Assoluto Vs Errore relativo
>in ambito ingegneristico/scientifico l _errore relativo_ è spesso più importante di quello assoluto siccome quest ultimo non dipende dal ordine di grandezza che si sta considerando e puo dare informazioni poco rilevanti
>> [!example]- 
>> se si considerano distanze astronomiche avere un errore assoluto di 1 cm o di 1 km non è molto significativo mentre l errore relativo ci da una informazione qualitativa molto piu significativa

nella rappresentazione dei numeri reali in [[Insieme dei numeri di macchina|numeri di macchina]] si possono verificare 2 casi
- $|x|< \omega$ si ha un _Underflow_ e $|x|>\Omega$ si ha un _Overflow_ 
	- Sono casi in cui il numero che si vuole rappresentare non è rappresentabile in quel specifico insieme di macchina, provando a fare la rappresentazione si ottengono risultato imprevedibili
- $\omega < |x| < \Omega$
	- caso di numeri rappresentabili ma sempre ammettendo un errore di rappresentazione 
		- _Possibili tipi di approssimazione_:
			1. _round to the nearest_ (arrotondamento): il numero $x$ viene approssimato con il numero rappresentabile $\tilde x$ più vicino
			2. _round toward zero_ (troncamento): il numero $x$ viene approssimato con il più grande numero rappresentabile $\tilde x$ il cui valore assoluto risulti minore od uguale al valore assoluto di $x$
			3. _round toward plus infinity_: il numero $x$ viene approssimato al più piccolo numero rappresentabile maggiore del dato
			4. _round toward minus infinity_: il numero $x$ viene approssimato al più grande numero rappresentabile minore del dato

### Definizioni
- $trn(x) = \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite _troncamento_ della parte decimale non rappresentabili  
- $arr(x)= \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite l _arrotondamento_ al numero di macchina più vicino 

### Teorema errore assoluto
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
_sia_ $a = \beta^p\alpha$ un _numero di macchina_ qualsiasi e $b = \beta^p(\alpha + \beta^{-t})$ più _piccolo numero di marchiana_ successore di $a$ abbiamo che $|b-a| = \beta^{p-t}$
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

### Teorema errore relativo
_sia_ $x \in \mathbb{R}$ 
_se_  $\omega \leq |x|\leq \Omega$ ovvero non ci sono casi di _overflow_ o _underflow_ 
_allora_ vale
$$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} < u = 
\begin{cases}
\beta^{1-t} &\text{if} &\tilde  x = trn(x)\\
\frac{1}{2}\beta^{1-t} & \text{if}& \tilde x = arr(x)
\end{cases}
$$
la quantità $u$ è detta _precisione di macchina_ 
##### Dimostrazione
- Sappiamo che $x \geq \beta^{p-1}$
	- siccome $x=\beta^p(\sum^\infty_{i=1}d_{i}\beta^{-i})$ e $\beta^{p-1}= \beta^p(10\dots0)_t$
	- essenzialmente stiamo dicendo che $x$ è maggiore del valore con solo con stesso esponente ma con valore della mantissa  più piccola possibile
- _Troncamento_: $\tilde x = trn(x)$
	- Sappiamo che $|\tilde x-x| < \beta^{p-t}$ dal _teorema del errore assoluto_$$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} < \frac{\beta^{p-t}}{\beta^{p-1}}=\beta^{1-t}$$
- _Arrotondamento_: $\tilde x = arr(x)$
	- Sappiamo che $|\tilde x-x| < \frac{1}{2} \beta^{p-t}$ dal _teorema del errore assoluto_ $$|\epsilon_x|=\frac{|\tilde x-x|}{|x|} < \frac{\frac{1}{2}\beta^{p-t}}{\beta^{p-1}} = \frac{1}{2}\beta^{1-t}$$
## Precisione di macchina
la quantità $u = \beta^{1-t}$ detta _precisione di macchina_ ha le seguenti proprietà
- è _indipendente_ dalla grandezza del numero 
- è una _caratteristica_ del [[Aritmetica di Macchina|aritmetica di macchina]] ovvero dipende dal 
	- Insieme dei [[Insieme dei numeri di macchina|numeri rappresentabili]] 
	- Tecnica di approssimazione
mentre la funzione che esprime il legame tra un numero reale e la sua _rappresentazione in macchina_ $fl(x)=x(1+\epsilon_x)$ con $|\epsilon_x| \leq u$  con un qualsiasi metodo di approssimazione
- $\epsilon_x$ dipende dal metodo di approssimazione il che fa variare il valore finale di macchina 
	- _arrotondamento_: segno dipendente dal $x$
	- _troncamento_: $\epsilon_x < 1$

> [!tips]- Controllare qual è la precisione di macchina
> Per valutare la precisione di macchina possiamo determinare il piu piccolo numero di macchina maggiore di $1$. Detto infatti $x$ tale numero abbiamo che $x − 1 = |x−1| = \beta^{1−t}$ essendo $1 = \beta^1 \cdot \beta^{−1}$ rappresentato con esponente $p = 1$. Il seguente script MatLab fornisce il valore richiesto 
> ```mathlab
>eps = 0.5
>eps1 = eps+1
>while(eps1>1)
>	eps =0.5*eps
>	eps1 = eps+1
>end
>eps = 2*eps
>```
>In sostanza, lo script funziona perché sfrutta le caratteristiche del sistema di numerazione floating-point utilizzato dal computer per calcolare la più piccola frazione rappresentabile. Il valore di eps calcolato dallo script rappresenta l'errore di rappresentazione minimo che può essere commesso durante i calcoli numerici sul computer.


### Operazioni di macchina
per le operazioni in numero di macchina si pone il problema del approssimazione dei risultati. solitamente il risultato di un operazione aritmetica tra [[Insieme dei numeri di macchina|numeri di macchina]] non è un numero di macchina ciò significa che va aggiunta un ulteriore approssimazione  

_definite_ $\oplus,\ominus,\otimes,\oslash$ rispettivamente somma, sottrazione, moltiplicazione e divisione tra _numeri di macchina_ 
_siano_ $\forall a,b \in \mathscr{F}(\beta,t,m,M)$ numeri di macchina
_se_  $\omega \leq |x|\leq \Omega$ ovvero non ci sono casi di _overflow_ o _underflow_  
_allora_ vale che 
$$a \oplus b  =  fl(a+b)  =   (a+b)(1+\epsilon_1) $$
con $|\epsilon_1| \leq u$ ed è detto _errore locale del operazione_

> [!tip]
> è spiegato con $\oplus$ ma vale per qualsiasi operazione

> [!warning] Operazioni classiche vs operazioni di macchina
> in generale nelle operazioni di macchina non vale
> 1. l'_associatività_ $a \oplus(b\oplus c) \not = (a \oplus b)\oplus c$

questa appena vista è nel ipotesi che i numeri siano gia di macchina ma si puo fare anche il caso in cui questi non lo siano. quindi
_siano_ $\forall a,b \in \mathbb{R}$ numeri reali
_se_  $\omega \leq |x|\leq \Omega$ ovvero non ci sono casi di _overflow_ o _underflow_  
_allora_ vale che 
$$
\begin{array} {}
fl(a)\oplus fl(b)  & = \\
\tilde a \oplus \tilde b & = \\
fl(\tilde a + \tilde b)  & = \\
(\tilde a + \tilde b)(1+\epsilon_1) & =\\
(a(1+\epsilon_a)+b(1+\epsilon_b))(1+\epsilon_1) & \dot = \\ (a+b) +a\epsilon_a+b\epsilon_b+ (a+b)\epsilon_1
\end{array}
$$
dove con il simbolo $\dot =$ si intende _l'uguaglianza  al primo ordine_  ovvero considerando le sole le componenti lineare negli errori e trascurando le componenti di ordine superiore al primo. Questa è chiamata _analisi del errore al primo ordine_. 

_siano_ $a,b \in \mathbb{R}$ numeri reali
_se_  
- $\omega \leq |x|\leq \Omega$ ovvero non ci sono casi di _overflow_ o _underflow_  
- $a+b \not = 0$
_allora_ l _errore relativo totale_ vale 
$$\epsilon_{tot}=\frac{\mu_{x}}{x}=\frac{\tilde{x}-x}{x}=\frac{fl(a+b)-(a+b)}{a+b} \dot = \frac{a}{a+b}\epsilon_a+\frac{b}{a+b}\epsilon_b+\epsilon_1$$
espandendo $fl(a+b)$ e con qualche passo algebrico si arriva a questo uguaglianza al _prim'ordine_. questa esprime la dipendenza dell’_errore totale_ commesso nel calcolo della somma tra due numeri reali rispetto agli [[Tipi di Errore nel calcolo numerico#Errori|errori]] generati dall’approssimazione dei dati iniziali detto _errore inerente_  $\epsilon_{a},\epsilon_{b}$ e agli errori generati dall’algoritmo di calcolo detto _[[Tipi di Errore nel calcolo numerico|errore algoritmico]]_ $\epsilon_{1}$



