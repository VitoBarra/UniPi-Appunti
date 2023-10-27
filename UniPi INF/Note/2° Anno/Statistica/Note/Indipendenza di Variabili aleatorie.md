---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Indipendenza di Variabili aleatorie
---
due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] $X$ e $Y$ sono dette _indipendenti_ se presi comunque $A$ e $B$ sottoinsiemi di $\mathbb{R}$ gli aventi $X^{-1}(A)$ e $Y^{-1}(B)$ sono indipendenti. cioè vale $$\mathcal{P}\{ X \in  A , Y \in  B \}=\mathcal{P}\{ X \in  A  \} \cdot \mathcal{P} \{ Y \in  B \}$$piu in generalele variabili $X_{1},\dots X_{n}:\Omega \rightarrow\mathbb{R}$ si dicono indipendenti se presi comunque $A_{1},\dots A_{n} \subseteq \mathbb{R}$ vale $$\mathcal{P}(X_{1}\in  A_{1},\dots X_{n} \in  A_{n})=\mathcal{P}(X_{1}\in  A_{1})\dots\mathcal{P}(X_{n} \in  A_{n}) $$
#### Proposizione
_siano_  $X$ e $Y$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] _discrete_ con immagine rispettivi nei punti $x_{i},y_{i}$ questi sono _indipendenti_ $\iff$ vale l e uguaglianza tra le _[[Probabilita sui numeri Reali#Funzione di massa (Definizione)|funzioni di massa]]_ $$p(x_{i},y_{i})=p(x_{i})p(y_{i}) \ \ \ \forall  (x_{i},y_{i}) $$
_siano_ $X,Y$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] _tali che_ $(X,Y)$ abbia _[[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita]]_, le due variabili sono _indipendenti_ $\iff$ vale l eguaglianza $$f(x,y)=f_{X}(x)\cdot f_{Y}(y)\ \ \ \ \forall  (x,y)$$

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



