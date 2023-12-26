---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili aleatorie - Covarianza e correlazione
---
la Covarianza delle [[Variabili Aleatorie (Casuali)|variabili aleatorie]] è un concetto analogo alla [[Statistica Descrittiva - Dati Multivariati#Covarianza definizione (definizione)|Covarianza]] nel caso dei dati multi variati in _[[Statistica descrittiva|statistica descrittiva]]_
#### Covarianza e coefficiente di correlazione (Definizione)
_siano_ $X$ e $Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] con [[Variabili aleatoria - Momenti|Momento secondo]] 
_allora_ è detto _covarianza_ il numero $$\begin{array}{}
Cov(X,Y) & = & \mathbb{E}[(X - \mathbb{E}[X])(Y-\mathbb{E}[Y])] & = \\
 & = & \mathbb{E}[XY]-\mathbb{E}[X]\mathbb{E}[Y]
\end{array}
$$
e _se_ $Var(X)\not=0$ e $Var(Y)\not=0$ 
_allora_ è detto _coefficiente di correlazione_ il numero $$\rho(X,Y)=\frac{Cov(X,Y)}{\sigma(X)\sigma(Y)}$$dove è la [[Funzione radice|radice]] della _[[Variabili aleatorie - Varianza|Varianza]]_ quindi $$\sigma(X)=\sqrt{Var(X)}= \sqrt{ \mathbb{E}[(X-E[X])^{2}] }$$ 
Quindi $Cov(X,Y)=0$ si ha $\rho(X,Y)=0$ e le due variabili sono dette _scorrelate_.
_valgono_ le seguenti proprieta
- $Cov(aX+bY+c,Z)=aCov(X,Z)+bCov(Y,Z)$
- $Cov(X,Y)=Cov(Y,X)$
- $Var(X)=Cov(X,X)$
- $Var(X+Y)=Var(X)+Var(Y)+2Cov(X,Y)$


#### Preposizione
_siano_ $X$ e $Y$ due [[Variabili Aleatorie (Casuali)|Variabili aleatorie]] 
_allora_ vale
- $|\rho(X,Y)| \leq 1$
- $\min_{a,b\in \mathbb{R}^{2}}\mathbb{E}[(Y-a-bX)^{2}]=Var(Y)\cdot (1-\rho(X,Y)^{2})$
_Dimostrazione_
	la prima priorità segue dalla _[[Diseguaglianza di Schwartz|diseguaglianza di Schwarz]]_$$\begin{array}{}
	| Cov(X,Y)|  & \leq \\
   \mathbb{E}[|X- \mathbb{E}[X]||Y-\mathbb{E}[Y]|]  & \leq \\
\sqrt{ \mathbb{E}[(X -\mathbb{E}[X])^{2}] } \sqrt{ \mathbb{E}[(Y-\mathbb{E}[Y])^{2}] }  & = \\
\sigma(X)\sigma(Y)   
\end{array}
	$$
	la seconda Proprietà invece si dimostra con lo stesso procedimento della [[Retta di regressione|retta di regressione]]


#### Teoria 
presi i $a_{*}$ e $b_{*}$ che realizzano $$\min_{a,b \in \mathbb{R}}\mathbb{E}[(Y-a-bX)^{2}]$$ la [[Retta|retta]] $y=a_{*}+b_{*}x$ è la _migliore_ approssimazione _lineare_ tra $X$ e $Y$ .
poiché il valore del minimo è _proporzionale_ al valore $1 - \rho^{2}$ e quindi piu $|\rho| \approx 1$ piu i valori sono ben approssimati da una [[Retta|retta]].
Il _coefficente di correlazione_ è la misura di  dipendenza _lineare_ tra $X$ e $Y$.
Due [[Variabili Aleatorie (Casuali)|variabili]] se sono _[[Indipendenza di Variabili aleatorie|indipendenti]]_ allora sono anche _scorrelate_ e $\rho =0$, non è necessariamente vero il contrario infatti il termine _lineare_ sta proprio ad indicare l approssimazione con una _retta_. Se questo non è possibile i dati potrebbero comunque risultare non _indipendenti_ ma _scorrelati_. 
Esempio $Y=X^{2}$
