---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili aleatoria - Momenti
---
sono dei valori “attorno” a cui la _[[Variabili Aleatorie (Casuali)|variabili aleatore]]_ si concentrano e riprendono le stesse idee di [[Statistica descrittiva - Dati Numerici|media e varianza]] per i semplici valori numerici

### Valore atteso (momento primo)
_Discreta_:
	_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] _discreta_ con la funzione di massa $p$ che assume i valori $x_{1},x_{2},\dots$
	_se_ vale che $\sum_{i}|x_{i}|p(x_{i}) < + \infty$ 
	_allora_ si dice che $X$ ha _valore atteso_ (detto momento primo) ed è il numero $$\mathbb{E}[X]=\sum_{i}x_{i}p(x_{i})$$
_con densita_:
	_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] _con densità_  $f$
	_se_ vale che $\int ^{+\infty}_{-\infty}|x|f(x) \, dx < +\infty$
	_allora_ si dice che $X$ ha _valore atteso_ ed è il numero $$\mathbb{E}[X]=\int ^{+\infty}_{-\infty}xf(x) \, dx $$


>[!tip]
>esiste una definizione generale ma richiede teoria del integrazione generale

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
	consideriamo gli insiemi $A_{i}=\{ j\mid g(x_{j}=y_{i}) \}$ e osservando che $P_{Y}(y_{i})=\sum_{j \in A_{i}}\mathcal{P}\{ X = x_{j} \}=\sum_{j \in A}P_{X}(x_{j})$. e quindi abbiamo a che fare cose serie e questo sono associative per cui vola $$
	\begin{array}{}
	\mathbb{E}[Y] & = &  \\
    \sum_{i}y_{i}p_{Y}(y_{i}) & = &\\  
    \sum_{i}y_{i}  \left( \sum_{j\in  A_i}p_{X}(x_{j}) \right)  & = & \\ \sum_{i}\left( \sum_{j \in  A_i}g(x_{j})p_{X}(x_{j}) \right)    & = & \\
    \sum_{j}g(x_j)p_X(x_j)
    \end{array}
	$$ cioe la tesi
	Il _caso generale_ si ottiene scrivendo la funzione g nella forma $g =g^{+}−g^{-}$ e sommando le relative serie (ricordiamo che con $g+(x) = \max(g(x),0)$ e $g−(x) = −\min(g(x),0)$ intendiamo la parte positiva e la parte negativa della funzione $g$)
	
##### Proprieta generali 
se la _[[Variabili Aleatorie (Casuali)|variabile discreta]]_ ha _valore atteso_ valgono le seguenti proprietà
-  $\forall a,b \in\mathbb{R}, \mathbb{E}[aX+b]=a\mathbb{E}[X]+b$, vale $\mathbb{E}[b]=b$
- $|\mathbb{E}[X]| \leq \mathbb{E}[|X|]$
- se $\mathcal{P}(X \geq 0)=1 \implies \mathbb{E}[X] \geq 0$

#### Mementi
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|Variabile Aleatoria]] , e $n> 0$ un numero 
_se_  $\mathbb{E}[|X|^{n}]<+\infty$ 
_allora_ il numero $\mathbb{E}[X^{n}]$ è detto _momento di ordine_ $n$ 

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
	 
  $$
  da cui $\mathbb{E}[|X|^{n}]< + \infty \implies \mathbb{E}[|X|^{m} < +\infty]$



