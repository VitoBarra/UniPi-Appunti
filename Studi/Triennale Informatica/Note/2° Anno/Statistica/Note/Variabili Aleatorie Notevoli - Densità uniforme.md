---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie Notevoli - Densità uniforme
---
#### Variabili uniformi su intervalli
la [[Variabili Aleatorie (Casuali)|variabile aleatoria]] definita uniforme è definita come
_siano_  $a <b$ dati due numeri reali
_allora_ la [[Variabili Aleatorie (Casuali)|densita]] _uniforme_ sul intervallo $[a,b]$ è costate sul intervallo e nulla al di fuori $$f(x)= \begin{cases}
	\frac{1}{b-a} & if  & a <x <b \\
0  & else & 
\end{cases}$$

#### Momenti e varianza
_sia_ $X$ _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_  _uniforme_   
_se_ una ha densità solo in un _intervallo limitato_ 
_allora_ questa sicuramente ha tutti i _momenti_. 
Abbiamo quindi che il _[[Variabili aleatoria - Momenti|momento primo]]_ valga $$\begin{array}{}
\displaystyle\mathbb{E}[X] & = &\displaystyle \int^{b}_{a}\frac{x}{b-a}  \ dx \\ & = & \displaystyle \left. \frac{x^{2}}{2(b-a)}  \right|^{a}_{b}&  \\ & 
= & \displaystyle \frac{b^{2}-a^{2}}{2(b-a)} & = & \cfrac{a+b}{2}
\end{array}$$ e con conti simili si ottiene [[Variabili aleatoria - Momenti|momento secondo]]   $$\begin{array}{}
\displaystyle\mathbb{E}[X^{2}] & = &\displaystyle \int^{b}_{a}\frac{x^{2}}{b-a}  \ dx \\ & = & \displaystyle \left. \frac{x^{3}}{3(b-a)}  \right|^{a}_{b}&  \\ & 
= & \displaystyle \frac{b^{3}-a^{3}}{3(b-a)} & = & \cfrac{a^{2}+ab+b^{2}}{3}
\end{array}$$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$Var(X)=\frac{(b-a)^{2}}{12}$$
e la [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] risulta $$M_{X}(t)=\frac{e^{bt}-e^{at}}{bt-at}$$