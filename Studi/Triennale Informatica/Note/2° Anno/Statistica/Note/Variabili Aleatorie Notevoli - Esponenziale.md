---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Esponenziale
---
la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_  __esponenziale__ ha [[Legge di Probabilita|Legge di Probabilita]] definita dalla __densita esponenziale__ di parametro $\lambda>0$ e questa è definita come $$f(x)=\begin{cases}
	\lambda e^{-\lambda x} &  x>0 \\
    0  & x \leq 0
\end{cases}$$
e si vede che la _[[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita]]_ è effettivamente una [[Definizione di Probabilita|probabilità]] con l espressone $$  \left .\int_{0}^{+\infty} \lambda e^{-\lambda x}  \, dx =-e^{-\lambda x}\right|_{0}^{+\infty}=1$$poiché la densita prende valori diversi da $0$ solo per $x$ positivi si ha che $\mathcal{P}\{X \leq 0  \}=0$

>[!tip]
>la variabile esponenzioale descrive _ad esempio_ il tempo di attesa tra due eventi aleatori

##### Teoria
la _variabile esponenziale_ è _[[Variabili aleatorie senza memoria|senza memeria]]_



#### Momenti e varianza
_sia_  $X$ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ _esponenziale_ di parametro $\lambda$ non si può dire a priori se questo accetta _[[Variabili aleatoria - Momenti|momento primo]]_ ma essendo una variabile positiva per $x$ _positivo_ vale che  $$\begin{array}{}
\displaystyle\mathbb{E}[X] & = &\displaystyle \int ^{+\infty}_{0}\lambda xe^{-\lambda x} \, dx  \\
& = & \displaystyle\frac{1}{\lambda}\int ^{+\infty}_{0}te^{-t} \, dt  
& =  &\displaystyle \frac{1}{\lambda}
\end{array}$$ e con conti simili si ottiene [[Variabili aleatoria - Momenti|momento secondo]]   $$\mathbb{E}[X^{2}]=\frac{2}{\lambda^{2}} $$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$Var(X)=\frac{2}{\lambda^{2}}-\left( \frac{1}{\lambda} \right)^{2}=\frac{1}{\lambda^{2}}
$$
e la funzione di [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] è $$M_{x}(t)=\left( 1-\frac{t}{\lambda} \right)^{-1}$$
