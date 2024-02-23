---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Binomiale
---
Consideriamo il caso in cui vogliamo trovate la _[[Probabilita sui numeri Reali|legge di probabilità]]_  della situazione in cui ci interessano solo _due esiti_ di una prova ripetuta $n$ volte _con rimpiazzo_
chiamiamo solo una due due esiti “_successo_”  e questa ha [[Definizione di Probabilita|probabilita]] $p\in (0,1)$

>[!tip]
>lo stesso caso _senza rimpiazzo_ è modellizzato dalla variaible [[Variabili Aleatorie Notevoli - Ipergeometrica|ipergiometrica]]
#### Variabile Binomiale
_sia_ $X:\Omega \rightarrow\{ 1,\dots,n\}$ la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ che _conta_ il numero di _successi_ __con rimpiazzo__
_se_ vale che $$\mathcal{P}(X=h)=\begin{pmatrix}n \\ h\end{pmatrix} p^{h}(1-p)^{n-h} \ \ \ \ , 0 \leq h\leq n$$
_allora_ è detta __variabile binomiale__ di parametri $n,p$ indicata con $B(n,p)$ 
dove 
- $p^{h}(1-p)^{n-h}$ è la probabilità che compaia un risultato con $h$ _successi_ e $(n-h)$ _insuccessi_. e questo vale per l _[[Indipendenza Stocastica|indipendenza]]_ dei risultati
- $\begin{pmatrix}n \\h \end{pmatrix}$ è il numero di modi di [[Combinatoria#Disposizioni|disporre]] gli $h$ _successi_ e $(n-h)$ _insuccessi_

la somma di tutte le probabilità ovvero la [[Definizione di Probabilita|probabilità]] totale  è $1$ come conseguenza del _binomiale_.


> [!tip]
> Questa definizione é identica al [[Polinomio di Bernstein|polinomio di bernstein]] 


> [!tip] Variabile di bernulli 
>con $n=1$ é identica alla _[[Variabili Aleatorie Notevoli - Bernulli|variabile di bernulli]]_ 


#### Momenti e varianza
una _variabile_ $X$ _Binomiale_ $B(n,p)$ può essere vista come somma di $n$ [[Variabili Aleatorie Notevoli - Bernulli|variabili di Bernulli]] $B(p)$ [[Indipendenza di Variabili aleatorie|indipendenti]] e si ha quindi che i [[Variabili aleatoria - Momenti|momenti]] _primi e secondi_ sono $$\begin{array}{}
\mathbb{E}[X] & = & np\\ \mathbb{E}[X^{2}] & = & np+np^{2}(n-1)
\end{array}
$$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$
\begin{array}{}
Var(X) & = & \mathbb{E}[X^{2}]-\mathbb{E}[X]^{2} \\
 & = & np+np^{2}(n-1)-n^{2}p^{2} \\
 & =  & np(1\cancel{ +np }-p\cancel{ -np }) \\
&=  & np(1-p) 
\end{array}
$$
e la [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] è $$M_{X}(t)=(pe^{t}+1-p)^{n}$$ 


#### Proposizione
_siano_ $X$ e $Y$ sono  [[Variabili Aleatorie (Casuali)|variabili aleatorie]] _[[Variabili Aleatorie Notevoli - Binomiale|Binomiali]]_ $B(n,p)$ e $B(m,p)$ 
_se_ sono _[[Indipendenza di Variabili aleatorie|indipendenti]]_ 
_allora_ la _variabile aleatoria_ $Z= X+Y$ è _binomiale_ $$Z\sim B(n+m,p)$$

_Dimostrazione_$$\begin{array}{}
	\mathcal{P}\{ Z =h \}  & =  \\
\mathcal{P}\{ X=h,Y=0 \} + \mathcal{P}\{ X=h-1,Y=1\} & = \\
\binom{n}{h}p^{h}(1-p)^{n-h}(1-p)+\binom{n}{h-1}p^{h-1}(1-p)^{n-h+1}p  & =\\
\binom{n+1}{h}p^{h}(1-p)^{n+1-h}
\end{array}$$
ovvero $Z$ è del tipo $B(n+1,p)$ e la dimostrazione si completa per [[Tipi di dimostrazione|induzione]]
