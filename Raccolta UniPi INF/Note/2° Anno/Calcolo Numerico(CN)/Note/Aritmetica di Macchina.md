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
>in ambito ingegneristico/scientifico l _errore relativo_ è piu importante di quello assoluto siccome quest ultimo non dipende dal ordine di grandezza che si sta considerando e puo dare informazioni poco rilevanti, 
>> [!example]- 
>> se si considerano distanze astronomiche avere un errore assoluto di 1 cm o di 1 km non è molto significativo mentre l errore relativo ci da una informazione qualitativa molto piu significativa

nella rappresentazione dei numeri reali in numeri di macchina si possono verificare 2 casi
- $|x|< \omega$ si ha un _Underflow_ e $|x|>\Omega$ si ha un _Overflow_ 
	- Sono casi in cui il numero che si vuole rappresentare non è rappresentabile in quel specifico insieme di macchina, provando a fare la rappresentazione si ottengono risultato imprevedibili
- $\omega < |x| < \Omega$
	- caso di numeri rappresentabili ma sempre ammettendo un errore di rappresentazione 
		- _Possibili tipi di approssimazione_:
			1. _round to the nearest_ (arrotondamento): il numero $x$ viene approssimato con il numero rappresentabile $\tilde x$ piu vicino
			2. _round toward zero_ (troncamento): il numero $x$ viene approssimato con il piu grande numero rappresentabile $\tilde x$ il cui valore assoluto risulti minore od uguale al valore assoluto di $x$
			3. _round toward plus infinity_: il numero $x$ viene approssimato al piu piccolo numero rappresentabile maggiore del dato
			4. _round toward minus infinity_: il numero $x$ viene approssimato al piu grande numero rappresentabile minore del dato

### Definizioni
- $trn(x) = \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite troncamento della parte cedimale non rapresentabili  
- $arr(x)= \tilde x$ è l approssimazione di un numero $x \in \mathbb{R}$ in numero di macchina $\tilde x \in \mathbb{F}$ tramite l arrotondamento al numero di macchina piu vicino 

### Teorema errore assoluto
 dato un numero reale $x$ che si vuole rappresentare in aritmetica di macchina, se non ci sono casi di _overflow_ o _underflow_ si ha che 
 - $|trn(x)-x| < \beta^{p-t}$
 - $|arr(x)-x| \leq \frac{1}{2}\beta^{p-t}$

##### Dimostrazione
- $x = \Omega \implies$
	- $trn(x)=arr(x)=x$
	- $trn(x)-x =0$
	- $arr(x) -x =0$
- $0 <x<\Omega \implies$
	- $a = \beta^p\sum^t_{i=1}\beta^i$
	- $b = \beta^p\sum^t_{i=1}\beta^i + \beta^{-t}$
	- $b-a = b^{p-t}$
	- $a \leq x < b$
		- puo coincidere con a perchè x potrebbe essere esattamente rapresetabile mentre a b ci si somma sempre qualcosa quindi x è sicuramente minore
	- $\tilde x = trn(x) = a$
		- $\mu_x = |trn(x)-x|=|a-x|<|a-b| = \beta^{p-t}$
		- siccome $trn(x) = a$ e sappiamo che $b$ è il [[Insieme dei numeri di macchina|numero di macchina]] successivo  al numero che rappresentare sappiamo che $|a-b|$ sarà sicuramente maggiore di $|a-x|$. $|a-b|$ sappiamo essere uguale a $\beta^{p-t}$
	- $\tilde x = arr(x) = \begin{cases} a \text{ if } x < \frac{a+b}{2} \\ b \text{ if } x \geq \frac{a+b}{2}  \end{cases}$
		- $\mu_x = |arr(x)-x|\leq \frac{b-a}{2} = \frac{1}{2} \beta^{p-t}$
		- il numero reale è sempre tra due numeri di macchina e siccome l arrotondamento porta al piu vicino numero di macchina la distranza sara sempre minore della meta o uguale se il numero di macchina è esattamente a meta $= \frac{b-a}{2}$ 

### Teorema errore relativo
sia $x \in \mathbb{R}$ con $\omega \leq |x| \leq \Omega$ si ha 
$$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} < u = 
\begin{cases}
\beta^{1-t} &\text{if} &\tilde  x = trn(x)\\
\frac{1}{2}\beta^{1-t} & \text{if}& \tilde x = arr(x)
\end{cases}
$$
la quantità $u$ è detta _precisione di macchina_ 
##### Dimostrazione
- _Troncamento_: $\tilde x = trn(x)$
	- Sappiamo che $|\tilde x-x| < \beta^{p-t}$
	- Sappiamo che $x \geq \beta^{p-1}$
		- siccome $x=\beta^p(\sum^\infty_{i=1}\beta^{-1})$ e $\beta^{p-1}= \beta^p(10\dots0)_t$
		- essenzialmente stiamo dicendo che x è maggiore del valore con solo con stesso esponente ma con valore della mantissa  più piccola possibile
	- $$|\epsilon_x| = \frac{|\tilde x-x|}{|x|} < \frac{\beta^{p-t}}{\beta^{p-1}}=\beta^{1-t}$$
- _Arrotondamento_: $\tilde x = arr(x)$
	- Sappiamo che $|\tilde x-x| < \frac{1}{2} \beta^{p-t}$
	- Sappiamo che $x \geq \beta^{p-1}$
		- $$|\epsilon_x|=\frac{|\tilde x-x|}{|x|} < \frac{\frac{1}{2}\beta^{p-t}}{\beta^{1-t}} = \frac{1}{2}\beta^{1-t}$$



## Precisione di macchina
la quantita $u = \beta^{1-t}$ detta _precisione di macchina_ ha le seguenti proprieta
- è _indipendente_ dalla grandezza del numero 
- è una _caratteristica_ dell aritmetica i floating point
	- ovvero del insieme dei numeri rappresentabili e della tecnica di approssimazione
- $fl(x)=x(1+\epsilon_x)$ con $|\epsilon_x| \leq u$ , questa relazione esprime il modo in cui viene descritto il legame tra un numero reale e la sua rappresentazione in macchina
	- $\epsilon_x$ dipende dal metodo di approssimazione il che fa variare il valore finale di macchina 
		- _troncamento_: $\epsilon_x < 1$
		- _arrotondamento_: segno dipendente dal numero

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
per le operazioni in numero di macchina si pone il problema dell approssimazione dei risultati. solitamente il risultato di un operazione aritmetica tra [[Insieme dei numeri di macchina|numeri di macchina]] non è un numero di macchina ciò significa che va aggiunta un ulteriore approssimazione  

definite $\oplus,\ominus,\otimes,\oslash$ rispettivamente somma, sottrazione, moltiplicazione e divisione tra numeri di macchina possiamo scrivere che in _Assenza_ di situazioni di _overflow_ e _underflow_
$$
\begin{align}
\forall a,b \in \mathscr{F}(\beta,t,m,M) \\ a \oplus b=fl(a+b)= (a+b)(1+\epsilon_1)\\ |\epsilon_1| \leq u
\end{align}
$$
dove $\epsilon_1$ è detto _errore locale del operazione_, è spiegato con $\oplus$ ma vale per qualsiasi operazione

> [!warning] proprita che non sono piu vere
> in generale non siamo più nei numeri reali e non valgono più le proprietà dei numeri classici quindi potremmo avere 
> - _non associativita_ $a \oplus(b\oplus c) \not = (a \oplus b)\oplus c$



Se $a,b \in \mathbb{R}$  in essenza di situazione di _overflow_ ad _underflow_ si ha
$$
\begin{align}
a+b= \\
fl(a)\oplus fl(b) = \\
\tilde a \oplus \tilde b= \\
fl(\tilde a + \tilde b) = \\
(\tilde a + \tilde b)(1+\epsilon_1)\\
(a(1+\epsilon_a)+b(1+\epsilon_b))(1+\epsilon_1)\dot = \\ (a+b) +a\epsilon_a+b\epsilon_b+ (a+b)\epsilon_1
\end{align}
$$
dove il simbolo $\dot =$ si intende che l uguaglianza vale considerando le sole o componenti lineare negli errori e trascurando le componenti di ordine superiore al promo (chiamata _analisi del errore al primo ordine_). 
si ottiene quindi l _errore relativo totale_ che con $a,b \in \mathbb{R}, a+b \not = 0$  e in essenza di situazione di _overflow_ ad _underflow_ vale 
$$\frac{fl(a+b)-(a+b)}{a+b} \dot = \frac{a}{a+b}\epsilon_a+\frac{b}{a+b}\epsilon_b+\epsilon_1$$
espandendo $fl(a+b)$ e con qualche passo algebrico si arriva a questo uguaglianza al prim ordine. questa esprime la dipendenza dell’_errore totale_ commesso nel calcolo della somma tra due numeri reali rispetto agli [[Tipi di Errore nel calcolo numerico#Errori|errori]] generati dall’approssimazione dei dati iniziali detto _errore inerente_  (i primi due termini) e agli errori generati dall’algoritmo di calcolo detto _errore algoritmico_ 
(l ultimo termine)



