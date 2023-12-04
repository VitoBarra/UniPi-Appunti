---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Diseguaglianza di Markov
---
#### Diseguaglianza di Markov
_sia_ $X$ è una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ discreta o con densita a valori positivi e $a>0$ un numero.
_allora_ la _diseguaglianza di markov_ dice $$a\mathcal{P}\{ X\geq a \}\leq \mathbb{E}[X]$$
_Dimostrazione_:
	vanno separati due casi _discreti_ e _con densita_
_caso discreto_:$$\begin{array}{}
\mathbb{E}[X] & = &  \displaystyle\sum^{+\infty}_{i=1}x_{i}\mathcal{P}(X=x_{i})   \\ &\geq &\displaystyle  
\sum^{+\infty}_{i=1}\mathcal{P}(X=x_{ })\cdot\begin{cases}
a  & if & x_{i}\geq a \\
0  & if  & x_{i} < a_{i}  \\
\end{cases} & \\  & = & \displaystyle
\sum^{+\infty}_{i:x_{i}\geq a}a\mathcal{P}(X=x_{i}) &  \\
 & = & a\mathcal{P}(x \geq a)
\end{array}$$
_dimostazione con densita_:$$\begin{array}{}
\mathbb{E}[X] & = &\displaystyle   
\int ^{+\infty}_{0}tf_{X}(t) \, dt    \\ &\geq  & \displaystyle
\int ^{+\infty}_{a}tf_{X}(t) \, dt      \\ & \geq & \displaystyle
\int ^{+\infty}_{a}af_{X}(t) \, dt    &   =  & a \mathcal{P}\{ X \geq a \}
\end{array}$$e questa dimostrazione funziona indipendentemente dalla esistenza dei [[Variabili aleatoria - Momenti|momenti]]
