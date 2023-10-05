---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Indipendenza di Variabili aleatorie Multivariate
---
due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] $X$ e $Y$ sono dette _indipendenti_ se presi comunque $A$ e $B$ sottoinsiemi di $\mathbb{R}$ gli aventi $X^{-1}(A)$ e $Y^{-1}(B)$ sono indipendenti. cioè vale $$\mathcal{P}\{ X \in  A , Y \in  B \}=\mathcal{P}\{ X \in  A  \} \cdot \mathcal{P} \{ Y \in  B \}$$piu in generalele variabili $X_{1},\dots X_{n}:\Omega \rightarrow\mathbb{R}$ si dicono indipendenti se presi comunque $A_{1},\dots A_{n} \subseteq \mathbb{R}$ vale $$\mathcal{P}(X_{1}\in  A_{1},\dots X_{n} \in  A_{n})=\mathcal{P}(X_{1}\in  A_{1})\dots\mathcal{P}(X_{n} \in  A_{n}) $$
##### Proposizione
date due variabili $X$ e $Y$, con immagine rispettivi nei punti $x_{i},y_{i}$ questi sono _indipendenti_ $\iff$ vale l e uguaglianza tra le funzioni di massa $$p(x_{i},y_{i})=p(x_{i})p(y_{i}) \ \ \ \forall  (x_{i},y_{i}) $$Date due variabili $X,Y$ tali che $(X,Y)$ abbia densita, le due variabili sono _indipendenti_ $\iff$ vale l eguaglianza $$f(x,y)=f_{X}(x)\cdot f_{Y}(y)\ \ \ \ \forall  (x,y)$$

_Dimostrazione_
	andrebbero divise nei due tipi di cosa
_caso discreto_
	prendendo $A= \{ x_{i} \}$ e $B= \{ y_{j} \}$ si ha $$
\begin{array}{}
 p(x_{j},y_{j}) & = & \mathcal{P}\{ X=x_{i},Y=y_{j}\}  & = \\
\mathcal{P}\{ X =x_{i} \}\mathcal{P}\{ Y =Y_{j} \} & = & p(x_{i})p(y_{j})
\end{array}
$$e presi due sotto insiemi $A$ e $B$ di $\mathbb{R}$ si ha $$
\begin{array}
\mathcal{P}\{X \in  A,Y \in B \}=\displaystyle\sum_{x_{i}\in A,y_{j} \in  B} p(x_{i},y_{j}) \\
 \displaystyle\sum_{x_{i} \in  A}\displaystyle\sum_{y_{i} \in  B} p_{X}(x_{i})p_{Y}(y_{j})  & =  \\ \left( \displaystyle\sum_{x_{i} \in  A}p_{X}(x_{i}) \right)\left( \displaystyle\sum_{y_{i} \in  B} p_{Y}(y_{j}) \right)  & = \\
 \mathcal{P}\{ X \in  A \} \mathcal{P}\{ Y \in  B \}
\end{array}
$$ _da cui la tesi_




##### Proposizione
_siano_ $X$ e $Y$ sono rispettivamente variabili aleatorie _[[Variabili Aleatorie Notevoli|Binomiali]]_ $B(n,p)$ e $B(m,p)$ 
_se_ sono _indipendenti_ 
_allora_ la _variabile aleatoria_ $Z= X+Y$ è _binomiale_ $B(n+m,p)$ 

_Dimostrazione_
	$$\begin{array}{}
	\mathcal{P}\{ Z =h \}  & =  \\
\mathcal{P}\{ X=h,Y=0 \} + \mathcal{P}\{ X=h-1,Y=1\} & = \\
\binom{n}{h}p^{h}(1-p)^{n-h}(1-p)+\binom{n}{h-1}p^{h-1}(1-p)^{n-h+1}p  & =\\
\binom{n+1}{h}p^{h}(1-p)^{n+1-h}
\end{array}$$
ovvero $Z$ è del tipo $B(n+1,p)$ e la dimostrazione si completa per [[Tipi di dimostrazione|induzione]]


##### Proposizione
_siano_  $X,Y:\Omega \rightarrow \mathbb{N}$  _[[Variabili Aleatorie (Casuali)|variabili aleatorie]] discrete_ a valori naturali  _indipendenti_ e $Z=X+Y$ e siano $p_{X},p_{Y},p_{Z}$ le rispettive _funzioni di massa_
_allora_ vale che $$p_{Z}(n)=\sum_{h=0}^{n}p_{X}(h)\cdot p_{Y}(n-h)$$ 
_dimostrazione_
	questa equazione è una conseguenza della seguente e uguaglianza insiemistica$$\{ Z=n \}=\bigcup^{n}_{h=0}\{ X = h,Y= n-h\} $$e di conseguenza $$
	\begin{array}{}
    p_{Z}(n)=\mathcal{P}\{ Z=n \} & = \\
\displaystyle\sum^{n}_{h=0}\mathcal{P}\{ X=h\}\mathcal{P}\{ Y=n-h \}  & = \\
\displaystyle\sum^{n}_{h=0}p_{X}(h)p_{Y}(n-h)
\end{array}
$$
dove il secondo passaggio fa uso dell indipendeza



#### Formula della convoluzione
_siano_ $X,Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] con densità $f_{X},f_{Y}$ _indipendenti_ 
_sia_ $Z=X+Y$ 
_allora_ la variabile $Z$ ha densità $$
\begin{array}{}
f_{Z}= \\
\displaystyle\int ^{+\infty}_{-\infty}f_{X}(x)f_{Y}(z-x) \, dx = \\
\displaystyle\int ^{+\infty}_{-\infty}f_{Y}(y)f_{X}(z-y) \, dy 

\end{array}
$$
_dimostrazone_
	Osserviamo che $$
	\begin{array}{}
	A_{z} & = & \{ (x,y) \in  \mathbb{R}^{2}: x+y \leq z \} \\
 & = &  \{ (x,y)\in  \mathbb{R}^{2}: x \leq z-y \}
   \end{array}
	$$e dunque la _funzione di ripartizione_ di $Z$ è data da $$\begin{array}{}
F_{Z}  & = & \mathcal{P}\{ X+Y \leq z\}  & = \\ &  & 
\displaystyle\int \int_{A_{z}}f_{X}(x)f_{Y}(y)  \, dx  \, dy  & = \\ &  & 
\displaystyle\int_{-\infty}^{+\infty}  \left( \int^{z-y}_{-\infty}f_{X}(x)  \, dx  \right)f_{Y}(y)\, dy  & = \\ &  & 
\displaystyle\int_{-\infty}^{+\infty}\left( \int^{z}_{-\infty}f_{X}(x’-y)  \, dx’  \right)  f_{Y}(y)\, dy 
\end{array}$$
dove $x’=x+y$ e da qui la tesi deriva immediatamente [[Derivate|derivando]] in $z$ sotto il segno di [[Integrali|integrarle]] 
