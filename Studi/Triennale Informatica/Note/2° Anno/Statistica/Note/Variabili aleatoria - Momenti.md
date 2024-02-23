---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili aleatoria - Momenti
---
sono dei valori “attorno” a cui la _[[Variabili Aleatorie (Casuali)|variabili aleatore]]_ si concentrano e riprendono le stesse idee di [[Statistica descrittiva - Dati Numerici|media e varianza]] per i semplici [[Statistica descrittiva - Dati Numerici|valori numerici]]

#### Valore atteso (momento primo)
_Discreta_:
	_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] _discreta_ con la _funzione di massa_ $p$ che assume i valori $x_{1},x_{2},\dots$
	_se_ vale che $\sum_{i}|x_{i}|p(x_{i}) < + \infty$ 
	_allora_ si dice che $X$ ha _valore atteso_ (detto momento primo) ed è il numero $$\mathbb{E}[X]=\sum_{i}x_{i}p(x_{i})$$
_con densita_:
	_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] _con densità_  $f$
	_se_ vale che $\int ^{+\infty}_{-\infty}|x|f(x) \, dx < +\infty$
	_allora_ si dice che $X$ ha _valore atteso_ ed è il numero $$\mathbb{E}[X]=\int ^{+\infty}_{-\infty}xf(x) \, dx $$


>[!tip]
>esiste una definizione generale ma richiede [[Teoria del integrazione generale|teoria del integrazione generale]]

##### Con trasformazione
Si puo calcolare il _valore atteso_ anche di una [[Variabili Aleatorie (Casuali)|variabile aleatoria]]  trasformata con la [[Trasformazioni di variabili con densita|regola di cambio di variabile]] 

_discreto_:
	_sia_ $X$ una _variabile aleatoria discreta_ e consideriamo la variabile  $Y=g(x)$  con $g$ una [[Funzioni|funzione]]
	_se_ $\sum_{i}|g(x_{i})|p(x_{i})< +\infty$
	_allora_ il _valore atteso_ diventa $$\mathbb{E}[g(X)]=\sum_{i}g(x_{i})p(x_{i})$$
_con densita_:
	_sia_ $X$ una _variabile aleatoria con densità_ $f$
	_se_ vale che  $\int ^{+\infty}_{-\infty}|g(x)|f(x) \, dx < +\infty$ 
	_allora_ il _valore atteso_ diventa $$\mathbb{E}[g(X)]=\int ^{+\infty}_{-\infty}g(x)f(x) \, dx$$
_Dimostrazione_:
vanno distinti i due casi
_Discreto_:
	supponendo che $g(x_i)$ sia a valori _positivi_, allora la _variabile aleatoria_ $Y=g(X)$ assume valori $y_{1},y_{2},\dots$  che è un insieme _finito_ o [[Insiemi infiniti numerabili|numerabile]].
	consideriamo gli insiemi $A_{i}=\{ j\mid g(x_{j}=y_{i}) \}$ e osservando che $P_{Y}(y_{i})=\sum_{j \in A_{i}}\mathcal{P}\{ X = x_{j} \}=\sum_{j \in A}P_{X}(x_{j})$. e quindi abbiamo a che fare con [[Serie|serie]] e questo essendo [[Proprietà del operazioni - Associativà|associative]] vale $$
	\begin{array}{}
	\mathbb{E}[Y] & = &  \\
    \sum_{i}y_{i}p_{Y}(y_{i}) & = &\\  
    \sum_{i}y_{i}  \left( \sum_{j\in  A_i}p_{X}(x_{j}) \right)  & = & \\ \sum_{i}\left( \sum_{j \in  A_i}g(x_{j})p_{X}(x_{j}) \right)    & = & \\
    \sum_{j}g(x_j)p_X(x_j)
    \end{array}
	$$ cioe la tesi
	Il _caso generale_ si ottiene scrivendo la funzione g nella forma $g =g^{+}−g^{-}$ e sommando le relative serie (ricordiamo che con $g^+(x) = \max(g(x),0)$ e $g^−(x) = −\min(g(x),0)$ intendiamo la parte positiva e la parte negativa della funzione $g$)
	
##### Proprieta generali 
se la _[[Variabili Aleatorie (Casuali)|variabile discreta]]_ ha _valore atteso_ valgono le seguenti proprietà
-  $\forall a,b \in\mathbb{R}, \mathbb{E}[aX+b]=a\mathbb{E}[X]+b$, vale $\mathbb{E}[b]=b$
- $|\mathbb{E}[X]| \leq \mathbb{E}[|X|]$
- se $\mathcal{P}(X \geq 0)=1 \implies \mathbb{E}[X] \geq 0$


#### Mementi
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|Variabile Aleatoria]] , e $n> 0$ un numero 
_se_  $\mathbb{E}[|X|^{n}]<+\infty$ 
_allora_ il numero $\mathbb{E}[X^{n}]$ è detto _momento di ordine_ $n$ con formula _discreta_:$$\mathbb{E}[X^{ n}]=\sum_{i}x_{i}^{n}p_{X}(x_{i})$$e formula _continua_: $$\mathbb{E}[X^{n}]=\int ^{+\infty}_{-\infty}x^{n}f(x) \, dx $$

#####  Proposizione 
_siano_ $1 \leq m < n$ 
_se_ $\mathbb{E}[|X|^{n}] < + \infty$ 
_allora_ anche $\mathbb{E}[|X|^{m}] < +\infty$  


_Dimostrazione_:
	_dimostrazione_ generale si usa la _diseguaglianza di jensen_ dalla quale si ricava il risultato $$\mathbb{E}[|X|^{m}]^{1/m} < \mathbb{E}[|X|^{n}]^{1/n}$$
	_dimostazione_ nel caso discreto
	 partendo dal fatto fatto che $|t|^{m} \leq |t|^{n}+1$ si ha $$
    \begin{array}{} 
     \sum_{x_i}|x_{i}|^{m}p(x_{i})  & \leq  \\ \sum_{x_i}(|x_i|^{n}+1)p(x_i)  & =  \\
 \sum_{x_{i}}|x_{i}|^{n}p(x_{i}) +\sum_{x_{i}}p(x_{i})  & < & +\infty
     

    \end{array}
	 
  $$da cui $\mathbb{E}[|X|^{n}]< + \infty \implies \mathbb{E}[|X|^{m} < +\infty]$



### Momenti di due variabili
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


>[!tip]
>in generale $XY$ non è detto che abbia valore atteso ma abbiamo dei criteri, usando la [[Diseguaglianza di Schwartz|diseguaglianza di Schwartz]] otteniamo che se $X$ e $Y$ hanno [[Variabili aleatoria - Momenti|memento secondo]] allora $XY$ ha _sicuramente_ _valore atteso_ 

##### Corollario
se le due [[Variabili Aleatorie (Casuali)|variabili]] $X$ e $Y$ hanno _[[Variabili aleatoria - Momenti|momento secondo]]_ allora queste sono _[[Variabili aleatorie - Covarianza e correlazione|scorrelate]]_
#### Proposizione 3
_siano_ $X$ e $Y$ _[[Variabili Aleatorie (Casuali)|variabili aleatoria]]_ 
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]] 
_allora_ $\forall h,k :\mathbb{R} \rightarrow \mathbb{R}$ vale $$h(X)\ \ \ k(Y)$$ sono _induipendenti_  e 
_se_ $h(X)$ e $k(Y)$ hanno _[[Variabili aleatoria - Momenti|valore atteso]]_ 
_allora_ vale che $$\mathbb{E}[h(X)k(Y)]=\mathbb{E}[h(X)]\cdot \mathbb{E}[k(Y)]$$


