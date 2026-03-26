---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili aleatoria - Valore atteso
---
il **Valore atteso** è un [[Operazioni algebriche|operatore]] su _[[Variabili Aleatorie (Casuali)|variabili aleatore]]_ 

sebbene esista una definizione generale che permette di definire entrambi i casi (che richiede la [[Teoria del integrazione generale|teoria del integrazione generale]] ) la **definizione** di **valore atteso** viene data separatamente per il caso **discreto** e **continuo** 

caso **_discreto_**:
	_sia_ $X$ una _variabile aleatoria discreta_ e consideriamo la variabile  $Y=g(x)$  con $g$ una [[Funzioni|funzione]]
	_se_ $\sum_{i}|g(x_{i})|p(x_{i})< +\infty$
	_allora_ il **_valore atteso_** è definito come  $$\mathbb{E}[g(X)]=\sum_{i}g(x_{i})p(x_{i})$$
caso **_continuo_**:
	_sia_ $X$ una **[[Variabili Aleatorie (Casuali)|variabile aleatoria]] con densità** $f$
	_se_ vale che  $\int ^{+\infty}_{-\infty}|g(x)|f(x) \, dx < +\infty$ 
	_allora_ il _valore atteso_ diventa $$\mathbb{E}[g(X)]=\int ^{+\infty}_{-\infty}g(x)f(x) \, dx$$
dove l' applicazione di una funzione ad una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] è giustificata dalla [[Trasformazioni di variabili con densita|regola di cambio di variabile]] che ne definisce anche nuova densità da applicare

Il **valore atteso** $\mathbb{E}[\cdot]$ è un [[Applicazioni Lineari|funzione lineare]]  quindi se la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_  $X$ ammette **_valore atteso_**
**allora** valgono le seguenti proprietà  
-  $\forall a,b \in\mathbb{R}, \mathbb{E}[aX+b]=a\mathbb{E}[X]+b$, vale $\mathbb{E}[b]=b$ 
- $|\mathbb{E}[X]| \leq \mathbb{E}[|X|]$
- se $\mathcal{P}(X \geq 0)=1 \implies \mathbb{E}[X] \geq 0$



##### Coerenza con la variabile trasformata
Questa osservazione chiarisce che la scrittura $\mathbb{E}[g(X)]$ coincide con il valore atteso della variabile trasformata $Y=g(X)$.

_Proposizione_:
**sia** $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] discreta e sia $Y=g(X)$.
**Se** $Y$ ha **valore atteso**, 
**allora**$$\mathbb{E}[Y]=\mathbb{E}[g(X)]=\sum_{j} g(x_j)p_X(x_j)$$_Dimostrazione nel caso discreto_:
supponiamo prima che $g(x_j)\geq 0$. Allora $Y=g(X)$ assume valori $y_1,y_2,\dots$, che formano un insieme finito o [[Insiemi infiniti numerabili|numerabile]].

Per ogni $y_i$ consideriamo l'insieme$$A_i=\{j \mid g(x_j)=y_i\}$$Allora$$p_Y(y_i)=\sum_{j\in A_i} p_X(x_j)$$Di conseguenza$$
\mathbb{E}[Y]
= \sum_i y_i p_Y(y_i)
= \sum_i y_i\left(\sum_{j\in A_i} p_X(x_j)\right)
= \sum_i \left(\sum_{j\in A_i} g(x_j)p_X(x_j)\right)
= \sum_j g(x_j)p_X(x_j)
$$che e la tesi.

Il caso generale che comprende anche il continuo si ottiene scrivendo
$$
g=g^+-g^-,
$$
dove
$$
g^+(x)=\max(g(x),0), \qquad g^-(x)=-\min(g(x),0),
$$
e applicando il risultato alle due parti non negative.


#### Momenti
I **momenti** sono un caso particolare di [[Variabili aleatoria - Valore atteso|valore atteso]] e si ottengono scegliendo come trasformazione la funzione$$g(x)=x^n$$l **esponente** $n$ è detto **ordine del momento** è quindi il valore atteso di $X^n$, quando esiste è detto **momento di ordine** $n$

Dal punto di vista interpretativo, i momenti descrivono come la distribuzione è collocata e come i suoi valori si distribuiscono:
- il **momento primo** $n=1$ descrive la posizione media;
- il **momento secondo** $n=2$ è collegato alla dispersione;
- i momenti di ordine superiore descrivono aspetti più fini della forma della distribuzione.

Una proprietà dei **momenti**
_siano_ $1 \leq m < n$ 
_se_ $\mathbb{E}[|X|^{n}] < + \infty$ 
**_allora_** anche $\mathbb{E}[|X|^{m}] < +\infty$  
_Dimostrazione_:
	_dimostrazione_ generale si usa la _[[diseguaglianza di jensen|diseguaglianza di jensen]]_ dalla quale si ricava il risultato $$\mathbb{E}[|X|^{m}]^{1/m} < \mathbb{E}[|X|^{n}]^{1/n}$$
	_dimostrazione_ nel caso discreto
	 partendo dal fatto fatto che $|t|^{m} \leq |t|^{n}+1$ si ha $$
    \begin{array}{} 
     \sum_{x_i}|x_{i}|^{m}p(x_{i})  & \leq  \\ \sum_{x_i}(|x_i|^{n}+1)p(x_i)  & =  \\
 \sum_{x_{i}}|x_{i}|^{n}p(x_{i}) +\sum_{x_{i}}p(x_{i})  & < & +\infty
     

    \end{array}
	 
  $$da cui $\mathbb{E}[|X|^{n}]< + \infty \implies \mathbb{E}[|X|^{m} < +\infty]$



### Momenti di due variabili
Se $(X,Y)$ e una coppia di [[Variabili Aleatorie (Casuali)|variabili aleatorie]], si puo generalizzare il valore atteso a una funzione di due variabili.

_Sia_ $g:\mathbb{R}^2\to\mathbb{R}$.
_Se_ $g(X,Y)$ ha valore atteso,
_allora_ si definisce
$$
\mathbb{E}[g(X,Y)].
$$

Nel caso _discreto_, se $(X,Y)$ ha funzione di massa congiunta $p_{X,Y}(x_i,y_j)$, vale
$$
\mathbb{E}[g(X,Y)] = \sum_{i,j} g(x_i,y_j)\,p_{X,Y}(x_i,y_j).
$$

Nel caso _continuo_, se $(X,Y)$ ha densita congiunta $f_{X,Y}(x,y)$, vale
$$
\mathbb{E}[g(X,Y)] = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} g(x,y)\,f_{X,Y}(x,y)\,dx\,dy.
$$

In particolare, scegliendo $g(x,y)=x^m y^n$ si ottengono i **momenti misti**
$$
\mathbb{E}[X^m Y^n].
$$

#### Proposizione
_sia_ $X,Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] che ammettono **valore atteso** 
**alllora** [[Variabili aleatoria - Valore atteso|valore atteso]] e vale
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

la seconda proprieta si mostra considerando la [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X-Y$  e applicando le 


#### Proposizione 2
_siano_ $X$ e $Y$ due [[Variabili Aleatorie (Casuali)|variaibli aleatorie ]] che ammettano [[Variabili aleatoria - Valore atteso|valore atteso]]
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
>in generale $XY$ non è detto che abbia valore atteso ma abbiamo dei criteri, usando la [[Diseguaglianza di Cauchy-Schwartz|diseguaglianza di Schwartz]] otteniamo che se $X$ ha [[Variabili aleatoria - Valore atteso|memento secondo]] allora $XY$ ha _sicuramente_ _valore atteso_ 

##### Corollario
se le due [[Variabili Aleatorie (Casuali)|variabili]] $X$[[Variabili aleatoria - Valore atteso|momento secondo]] allora queste sono _[[Variabili aleatorie - Covarianza e correlazione|scorrelate]]_
#### Proposizione 3
_siano_ $X$ e $Y$ _[[Variabili Aleatorie (Casuali)|variabili aleatoria]]_ 
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]] 
_allora_ $\forall h,k :\mathbb{R} \rightarrow \mathbb{R}$ vale $$h(X)\ \ \ k(Y)$$ sono _induipendenti_  e 
_se_ $h(X)$ e [[Variabili aleatoria - Valore atteso|valore atteso]] 
_allora_ vale che $$\mathbb{E}[h(X)k(Y)]=\mathbb{E}[h(X)]\cdot \mathbb{E}[k(Y)]$$
