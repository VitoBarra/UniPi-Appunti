---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili aleatorie multivariate - Momenti
---
#### Proposizione
_sia_ $X,Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatori]] con [[Variabili aleatoria - Momenti|valori atteso]] 
_allora_ $X+Y$ ha [[Variabili aleatoria - Momenti|valore atteso]] e vale
- $\mathbb{E}[X+Y]=\mathbb{E}[X]+\mathbb{E}[Y]$
- se $X \geq Y$ _allora_ $\mathbb{E}[X]\geq\mathbb{E}[Y]$

_dimostrazione_:
	si dividono i due casi
_caso discrito_:
	$X+Y$ ha _valore atteso_ se $$\sum_{x_{i},y_{j}}|x_{i}+y_{j}|p(x_{i},y_{j}) < + \infty$$ ma $$\begin{array}{}
	\displaystyle\sum_{x_{i},y_{j}} |x_{i}+y_{j}|p(x_{i},y_{j}) &  \leq\\ 
    \displaystyle\sum_{x_{i},y_{j}} (|x_{i}|+|y_{j})|p(x_{i},y_{j})   & =\\  \displaystyle\sum_{x_{i}}|x_{i}|\sum_{y_{j}}p(x_{i},y_{j})+\sum_{y_{j}} |y_{j}|\sum_{x_{i}} p(x_{i},y_{j})  & =  \\ \displaystyle\sum_{x_{i}}|x_{i}|p_{X}(x_{i})+\sum_{y_{j}} |y_{j}| p_{Y}(y_{j})  &  <  \\
  + \infty
\end{array}$$
siccome le [[Serie|serie]] [[convergenza assoluta|convergono assolutamente]] possiamo togliere i valori assoluto e la diseguaglianza del primo passaggio diventa e uguaglianza e vale la tesi.

la seconda proprieta si mostra considerando la [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X-Y$  e applicando le _proprieta_ del [[Variabili aleatoria - Momenti|valore atteso]]


#### Proposizione 2
_siano_ $X$ e $Y$ due [[Variabili Aleatorie (Casuali)|variaibli aleatorie]] con [[Variabili aleatoria - Momenti|valore atteso]]
_se_ $X$ e $Y$ sono [[Indipendenza di Variabili aleatorie|indipendenti]]
_allora_ $XY$ ha _valore atteso_ e vale la formula$$\mathbb{E}[XY]=\mathbb{E}[X]\cdot  \mathbb{E}[Y]$$
_Dimostrazione_
vanno divisi i due casi
_caso discreto_$$\begin{array}{}
\displaystyle\sum_{x_{i},y_{j}}|x_{i}y_{j}|p(x_{i},y_{j}) & = \\
\displaystyle\sum_{x_{i},y_{j}}|x_{i}||y_{j}|p_{X}(x_{i})p_{Y}(y_{j})  & = \\ \displaystyle
\left( \sum_{x_{i}} |x_{i}|p_{X}(x_{i}) \right)\cdot\left( \sum_{y_{j}}|y_{j}|p_{Y}(y_{j}) \right)  &  <  & +\infty
\end{array}$$
che dimostra che $XY$ ha valore atteso e togliendo i valori assoluti si ottiene la formula $\mathbb{E}[XY]=\mathbb{E}[X]\cdot  \mathbb{E}[Y]$ come da tesi.


##### Corollario
se le due [[Variabili Aleatorie (Casuali)|variabili]] $X$ e $Y$ hanno _[[Variabili aleatoria - Momenti|momento secondo]]_ allora queste sono _scorrelate_
#### Proposizione 3
_siano_ $X$ e $Y$ _[[Variabili Aleatorie (Casuali)|variabili aleatoria]]_ 
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]] 
_allora_ $\forall h,k :\mathbb{R} \rightarrow \mathbb{R}$ vale $$h(X)\ \ \ k(Y)$$ sono _induipendenti_  e 
_se_ $h(X)$ e $k(Y)$ hanno _[[Variabili aleatoria - Momenti|valore atteso]]_ 
_allora_ vale che $$\mathbb{E}[h(X)k(Y)]=\mathbb{E}[h(X)]\cdot \mathbb{E}[k(Y)]$$

#### Diseguaglianza di Schwartz
_siano_ $X$ e $Y$ due _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ 
_allora_ vale $$\mathbb{E}[|XY|] \leq \sqrt{ \mathbb{E}[X^{2}] } \cdot \sqrt{ \mathbb{E}[Y^{2}] }$$
_dimostrazione_
	segue quella nel caso $\mathbb{R}^{2}$ 

>[!tip]
>in generale $XY$ non è detto che abbia valore atteso ma abbiamo dei criteri, per la [[Diseguaglianza di Schwartz|diseguaglianza di Schwartz]] se $X$ e $Y$ hanno [[Variabili aleatoria - Momenti|memento secondo]] allora $XY$ ha _sicuramente_ valore atteso 
