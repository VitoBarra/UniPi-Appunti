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
_se_ $X$ è una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ (discreta o con densita) a valori positivi e $a>0$
_allora_ $$a\mathcal{P}\{ X\geq a \}\leq \mathbb{E}[X]$$
_dimostrazione_:
	vanno separati due casi _discreti_ e _con densita_
_caso discreto_:
$$\begin{array}{}
\mathbb{E}[X]= \sum^{+\infty}_{i=1}x_{i}\mathcal{P}(X=x_{i})  & \geq  \\
\sum^{+\infty}_{i=1}\mathcal{P}(X=x_{ })\cdot\begin{cases}
a  & if & x_{i}\geq a \\
0  & if  & x_{i} < a_{i}  \\
\end{cases} & = \\
\sum^{+\infty}_{i:x_{i}\geq a}a\mathcal{P}(X=x_{i}) & =  \\
 a\mathcal{P}(x \geq a)
\end{array}$$
_dimostazione con densita_:

$$\begin{array}{}
\mathbb{E}[X] & = &   
\int ^{+\infty}_{0}tf_{X}(t) \, dt  & \geq \\ &  & 
\int ^{+\infty}_{a}tf_{X}(t) \, dt   &  \geq \\ &  & 
\int ^{+\infty}_{a}af_{X}(t) \, dt   &  =  & a \mathcal{P}\{ X \geq a \}
\end{array}$$
e la dimostrazione funziona indipendentemente dalla esistenza dei [[Variabili aleatoria - Momenti|momenti]]
