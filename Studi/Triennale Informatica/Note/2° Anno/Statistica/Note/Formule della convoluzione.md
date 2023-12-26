---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Formule della convoluzione
---
La  convoluzione è un [[Operazioni algebriche|Operazione]] solitamente denotata con $*$ e questa è un usata in vari contesti come nelle [[Convolutional neuronal Network]] che prendono il nome da quest operazione e nel _imagin Processing_ che li utilizza ampiamente. 


Quei ne viene mostrata l applicazione in _statistica_
#### Formula di convoluzione discreta
_siano_  $X,Y:\Omega \rightarrow \mathbb{N}$  _[[Variabili Aleatorie (Casuali)|variabili aleatorie]] discrete_ a valori naturali 
_se_ queste sono _[[Indipendenza di Variabili aleatorie|indipendenti]]_ 
_allora_ sia $Z=X+Y$ e siano $p_{X},p_{Y},p_{Z}$ le rispettive _[[Probabilita sui numeri Reali#Funzione di massa discreta (Definizione)|funzioni di massa]]_
_allora_ vale che $$p_{Z}(n)=\sum_{h=0}^{n}p_{X}(h)\cdot p_{Y}(n-h)$$ 
_dimostrazione_
	questa equazione è una conseguenza della seguente uguaglianza insiemistica$$\{ Z=n \}=\bigcup^{n}_{h=0}\{ X = h,Y= n-h\} $$e di conseguenza $$
	\begin{array}{}
    p_{Z}(n)=\mathcal{P}\{ Z=n \} & = \\
\displaystyle\sum^{n}_{h=0}\mathcal{P}\{ X=h\}\mathcal{P}\{ Y=n-h \}  & = \\
\displaystyle\sum^{n}_{h=0}p_{X}(h)p_{Y}(n-h)
\end{array}
$$
dove il secondo passaggio fa uso dell _[[Indipendenza di Variabili aleatorie|indipendeza]]_

>[!note]
>$n$ in questo contesto rappresenta una _somma fissa_ $y$ e $x$ con il vincolo $x+y=n$ infatti il parametro è della funzione di convoluzione è proprio il valore di questa somma e l output è la probabilita associata 



#### Formula della convoluzione continua
_siano_ $X,Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] con densità $f_{X},f_{Y}$ _[[Indipendenza di Variabili aleatorie|indipendenti]]_ 
_sia_ $Z=X+Y$ 
_allora_ la variabile $Z$ ha densità $$
\begin{array}{}
f_{Z}(z)= \\
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
F_{Z}  & =\\  \mathcal{P}\{ X+Y \leq z\}  & = \\  
\displaystyle\int \int_{A_{z}}f_{X}(x)f_{Y}(y)  \, dx  \, dy  & = \\  
\displaystyle\int_{-\infty}^{+\infty}  \left( \int^{z-y}_{-\infty}f_{X}(x)  \, dx  \right)f_{Y}(y)\, dy  & = \\  
\displaystyle\int_{-\infty}^{+\infty}\left( \int^{z}_{-\infty}f_{X}(x’-y)  \, dx’  \right)  f_{Y}(y)\, dy 
\end{array}$$
dove $x’=x+y$ e da qui la tesi deriva immediatamente [[Derivate|derivando]] in $z$ sotto il segno di [[Integrali|integrarle]] 


>[!tip] video 3B1B
>questo da un [idea visuale](https://youtu.be/IaSGqQa5O-M?si=H2xv8S8jRUAUTuHl) di cosa rappresentano le convoluzioni