---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic:
---

# Aritmetica di Macchina
---
Rappresentare un numero  $x \in \mathbb{R} ,x   \not =0$  in un [[Insieme dei numeri di macchina|numeri di macchina]] significa approssimare $x$ con un numero $\tilde{x} \in \mathbb{F}(\beta,t,m,M)$ commettendo un [[Tipi di Errore nel calcolo numerico#Errori|errore relativo di rappresentazione]]$$\epsilon_x=\frac{\tilde x-x}{x} = \frac{\mu_x}{x}$$dove la quantità $$\mu_x = \tilde x -x$$ è detto [[Tipi di Errore nel calcolo numerico#Errori|errore assoluto di rappresentazione]]

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


la funzione che esprime il legame tra un numero reale e la sua rappresentazione in [[Insieme dei numeri di macchina|numero di macchina]] e'  $$fl(x)=x(1+\epsilon_x)$$con con $|\epsilon_x| \leq u$ dove $u$ e' la [[Precisione di macchina|precisione di macchina]] e questo vale con un qualsiasi metodo di approssimazione
il valore $\epsilon_x$ dipende dal metodo di approssimazione  
- _arrotondamento_: segno dipendente dal $x$
- _troncamento_: $\epsilon_x < 1$


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



