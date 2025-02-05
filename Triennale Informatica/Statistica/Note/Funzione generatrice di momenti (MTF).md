---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Funzione generatrice di momenti (MTF)
---
Una _funzione generatrice di momenti_ [[Funzioni|funzione]]  che serve a calcolare direttamente il [[Variabili aleatoria - Momenti|momento]] $\mathbb{E}[X^{n}]$ con qualsiasi  [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X$ e $\forall n$

#### Funzione generatrice di momenti (Definizione)
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] 
_allora_ la _funzione generatrice di momenti_ è definita da $$M_{X}(t)=\mathbb{E}[e^{t X}]$$a questo punto [[Derivate|derivando]] si ottiene che $$M_{X}^{(n)}(t)=\frac{d^{n}M_{X}(t)}{dt^{n}}$$e da qui i momenti si ottengono _valutando_ l $n$- esima _derivata_ in 0 e risulta come 
$$\mathbb{E}[X^{n}]=M_{X}^{(n)}(0)$$
_dimostrazione_:
Questa formula viene dal fatto che l [[Espanzioni di funzioni in polinomi|espansione in polinomi]] di $$e^{tx}=\sum^{\infty}_{n=0}\frac{t^{n}}{n!}x^{n}$$ ed essendo i [[Variabili aleatoria - Momenti|momenti]] lineari otteniamo che $$\mathbb{E}[e^{tx}]=\sum^{+\infty}_{n=0}\frac{t^{n}}{n!}\mathbb{E}[X^{n}]$$questa è la definizione di $M_{x}(t)$ e [[Derivate|derivando]] per $t$ volte si ottiene che 
$$
M_{X}^{(n)}(t)=\frac{d^{n}\mathbb{E}[e^{tx}]}{dt^{n}} =   \sum^{n}_{h=0}0+\sum_{h=0}^{\infty}t^{h}\mathbb{E}[X^{n+h}]
$$
e _valutando_ in $t=0$ si ha che $$M_{X}^{(n)}(0) =\sum^{n}_{h=0}0+\mathbb{E}[X^{n}]+\sum^{\infty}_{h=0}0 = \mathbb{E}[X^{n}]$$da qui la _tesi_


#### Proposizione
_sia_ $X_{i},\dots,X_{n}$ un [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|campione idd]] 
_se_ $X_{1}$ ha una _funzione generatrice di momenti_ $M_{X_{1}}(t)$
_allora_ vale che $$M_{\sum_{i=1}^{n} X_{i}}(t)=\sum_{i=1}^{n} X_{i}=[M_{X_{1}}(t)]^{n}$$  