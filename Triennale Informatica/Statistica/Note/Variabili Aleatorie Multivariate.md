---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Multivariate
---
Le [[Variabili Aleatorie (Casuali)|Variabili Aleatorie]] _multivariate_ piu variabili aleatorie corrispettive ai [[Statistica Descrittiva - Dati Multivariati|Dati Multivariati]] e rappresentano più caratteri _qualitativi_  di un esperimento.

#### Variabile doppia (definizione)
_Sia_ ($\Omega,\mathcal{F},\mathcal{P}$) uno [[Definizione di Probabilità|spazio di probabilita]] e $X,Y$ due [[Variabili Aleatorie (Casuali)|Variabili aleatorie]] 
_allora_  la coppia di variabili possono essere viste come una funzione $$(X,Y):\Omega \rightarrow \mathbb{R}^{2}, \ \ \ \omega \in  \Omega \mapsto (X(\omega), Y(\omega)) \in  \mathbb{R}^{2}$$
##### Legge di probabilita (Definizone)
si definisce la _legge di probabilita_ della variabile aleatria doppia $(X,Y)$ come$$
\begin{array}
\mathcal{P}_{(X,Y)}(A)=\mathcal{P}(X,Y)\in  A  \\
\mathcal{P}\{\omega \in \Omega: X(w),Y(w) \in  A \}
\end{array} \ \ \ \ \ A \subseteq \mathbb{R}^{2}
$$Se $A=A_{1}\times A_{2}$ è un [[Insiemi Matematici|sottoinsieme]] _rettangolare_ , notiamo che $\{ (X,Y)\in A \} = \{ X \in A_{1}, Y \in A_{2}\}$ dove con la virgola si intende l inter senza di due condizioni $$
\begin{array}
\{ X \in  A_{1},Y \in  A_{2} \} & = &  \{ X \in A_1 \} \cap \{ Y \in A_2 \} \\
X^{-1}(A_{1}) \cap Y^{-1}(A_{2})  & = & (X,Y)^{-1}(A_{1}\times A_{2})  
\end{array}
$$
##### proprietà delle leggi di probabilità 
_sia_ $(X,Y)$ una [[Variabili Aleatorie (Casuali)|variabili aleatorie]] possiamo considerare separatamente le _leggi di probabilità_ $\mathcal{P}_{X}$ e $\mathcal{P}_{Y}$  chiamate _distribuzioni marginali_ della variabile doppie e vale che per ogni $A \subseteq \mathbb{R}$ ([[Insiemi Misurabili|misurabile]]) $$
\begin{array}
\mathcal{P}_{X}(A)=\mathcal{P}_{(X,Y)}(A \times \mathbb{R}) \\
\mathcal{P}_{Y}(A)=\mathcal{P}_{(X,Y)}(\mathbb{R} \times A)
\end{array}
$$ In particolare la _legge congiunta_ $\mathcal{P}_{(X,Y)}$ _determine univocamente_ le due _leggi marginali_ $\mathcal{P}_{X}, \mathcal{P}_{Y}$ ma non vale il contrario, Ci sono più modi per definire la legge congiunta a partire dalle _leggi marginali_

#### Variabili aleatorie doppie discrete
_sia_ $(X,Y)$ una _variabile aleatoria_ doppia
_se_ la sua immagine è un _[[Insiemi Matematici|insieme]] finito_ o _[[Insiemi infiniti numerabili|numerabile]]_ di punti $(x_{i},y_{i})$ 
_allora_ questa è detta _discreta_ e la sua [[Definizione di Probabilita|probabilita]] $\mathcal{P}_{(X,Y)}$ è definita dalla _funzione di massa_ $p(x_{i},y_{i})=\mathcal{P}\{ X=x_{i},Y=y_{i} \}$ e si ha che per  $A \subseteq \mathbb{R}^{2}$ $$\mathcal{P}_{(X,Y)}(A)=\mathcal{P}\{  (X,Y) \in  A\}=\sum_{(x_{i},y_{i})\in A}p(x_{i},y_{i})$$
##### Proposizione
Data una _variabile aleatoria doppia discreta_ $(X,Y)$ con _funzione di massa_ $p(x_{i},y_{i})$ le sue componenti sono _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ _discrete_ con funzioni di massa $$
\begin{array}{}
p_X(x_{i})=\sum_{y_j}p(x_{i},y_{i})\\ p_{Y}(y_{i})=\sum_{x_i} p(x_{i},y_{i})
\end{array}
$$
_dimostrazione_
	Notiamo che $\{ X =x_{i} \}=\bigcup_{j}\{ X=x_{i},Y=y_{j} \}$ e questi insiemi sono a due a due disgiunti e quindi vale$$
	\begin{array}{}
	 p_{X}(x_{i}) & = \\
     \mathcal{P}\{ X=x \} & =\\
     \sum_{y_{j}}\mathcal{P}\{ X=x_{i},Y = y_{j} \}  & =\\ \sum _{y_{j}}p(x_{i},y_{j})
    \end{array}
	$$ e l altra è analoga


#### Variabile doppia con densità (Definizione)
_sia_ $(X,Y)$ una _variabile aleatoria_ doppia
_se_ esiste una funzione $f:\mathbb{R}^{2}\rightarrow [0,\infty)$ [[Integrali|integrabile]] con $\int  \int_{\mathbb{R}^{2}} f(x,y) \, dx \, dy=1$ tale che 
_allora_ questa è detta _con densita_ e la sua [[Definizione di Probabilità|probabilità]] $\mathcal{P}_{(X,Y)}$ e si ha che per  $A \subseteq \mathbb{R}^{2}$ $$\mathcal{P}_{(X,Y)}(A)=\mathcal{P}\{  (X,Y) \in  A\}=\int  \int_{A} f(x,y) \, dx  \, dy $$
##### Proposizione
_se_ $(X,Y)$ ha _[[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita di probabilita ]]_ $f(x,y)$ anche $X$ e $Y$ ha _densita_ e sono $$\begin{array}{}
\displaystyle f_{X}(x)=\int ^{+\infty}_{-\infty}f(x,y) \, dy \\
\displaystyle f_{Y}(y)=\int ^{+\infty}_{-\infty}f(x,y) \, dx
\end{array}$$
quindi $f_{X}(x)=\int_{\mathbb{R}}f(x,y)  \, dy$ è la densita dalla _variabilita aleatoria_ $X$. Analogamente si ottiene la formula per la densita $f_{Y} =\int_{\mathbb{R}}f(x,y)  \, dx$

_se_ $X$ e $Y$ son _variabile aleatoria_ con densita non è detto che $(X,Y)$  abbia densita