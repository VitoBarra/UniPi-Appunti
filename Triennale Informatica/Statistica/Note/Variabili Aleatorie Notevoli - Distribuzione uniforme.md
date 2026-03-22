---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Distribuzione uniforme
---
la [[Variabili Aleatorie (Casuali)|variabile aleatoria]] notevole **uniforme** è definita come
_siano_  $a <b \in \mathbb{R}$ due numeri reali
_allora_ la [[Legge di Probabilita|legge di probabilita]] è definita dalla [[Variabili Aleatorie (Casuali)|densita]] che è  _uniforme_ sul intervallo $[a,b]$ è costate sul intervallo e nulla al di fuori  definendo  $$f(x)= \begin{cases}
	\frac{1}{b-a} & if  & a <x <b \\
0  & else & 
\end{cases}$$

#### Momenti e varianza
_sia_ $X$ _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_  _uniforme_   
_se_ una ha densità solo in un _intervallo limitato_ 
_allora_ questa sicuramente ha tutti i _momenti_. 
Abbiamo quindi che il _[[Variabili aleatoria - Momenti o Valore atteso|momento primo]]_ valga $$\begin{array}{}
\displaystyle\mathbb{E}[X] & = &\displaystyle \int^{b}_{a}\frac{x}{b-a}  \ dx \\ & = & \displaystyle \left. \frac{x^{2}}{2(b-a)}  \right|^{a}_{b}&  \\ & 
= & \displaystyle \frac{b^{2}-a^{2}}{2(b-a)} & = & \cfrac{a+b}{2}
\end{array}$$ e con conti simili si ottiene [[Variabili aleatoria - Momenti o Valore atteso|momento secondo]]   $$\begin{array}{}
\displaystyle\mathbb{E}[X^{2}] & = &\displaystyle \int^{b}_{a}\frac{x^{2}}{b-a}  \ dx \\ & = & \displaystyle \left. \frac{x^{3}}{3(b-a)}  \right|^{a}_{b}&  \\ & 
= & \displaystyle \frac{b^{3}-a^{3}}{3(b-a)} & = & \cfrac{a^{2}+ab+b^{2}}{3}
\end{array}$$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$Var(X)=\frac{(b-a)^{2}}{12}$$
e la [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] risulta $$M_{X}(t)=\frac{e^{bt}-e^{at}}{bt-at}$$
#### Funzione di distribuzione cumulativa
_sia_ $X$ _[[Variabili Aleatorie (Casuali)|variabile aleatoria]] uniforme_ su $[a,b]$ con densità

$$f(x)= \begin{cases}
\frac{1}{b-a} & a<x<b \\
0 & \text{altrimenti}
\end{cases}$$

la [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di distribuzione cumulativa]] è definita come$$F(x)=P(X\le x)=\int_{-\infty}^{x}f(t)\,dt$$poiché la densità è nulla fuori da $[a,b]$, il valore dell'integrale dipende dalla posizione di $x$ rispetto all'intervallo.

Se $x<a$ l'integrale non intercetta alcuna parte dell'intervallo di densità$$F(x)=0$$Se $a\le x\le b$ si integra solo sulla parte dell'intervallo fino a $x$$$F(x)=\int_{a}^{x}\frac{1}{b-a}\,dt=\frac{x-a}{b-a}$$Se $x>b$ si integra su tutto l'intervallo$$F(x)=\int_{a}^{b}\frac{1}{b-a}\,dt=1$$si ottiene quindi la forma esplicita$$F(x)=
\begin{cases}
0 & x<a \\
\dfrac{x-a}{b-a} & a\le x\le b \\
1 & x>b
\end{cases}$$la funzione di distribuzione cumulativa risulta quindi continua, crescente e lineare nell'intervallo $[a,b]$.