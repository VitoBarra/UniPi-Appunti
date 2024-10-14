---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Poisson
---

#### Variabile di Poisson
_sia_ $X:\Omega \rightarrow\mathbb{N}$ una  _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ nei naturali e $\lambda>0$ un numero 
_allora_ è $X$ una _variabile di Poisson_ 
_se_ vale $$\mathcal{P}(X=h)=e^{-\lambda}\frac{\lambda^{h}}{h!}$$questa è una [[Definizione di Probabilita|probabilità]] valida dobbiamo vedere che la probabilita totale è $1$ ma e deve quindi valere $$\sum^{+\infty}_{h=0}\mathcal{P}(X=h)=1$$ ma questa è una conseguenza dello sviluppo esponenziale $$e^{\lambda}=\sum^{+\infty}_{h=0}\frac{\lambda^{h}}{h!}$$
questa _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ approssima bene la variabile _[[Variabili Aleatorie Notevoli - Binomiale|binomiale]]_ $B(n,p)$ quando $n$ è grande e $p$ e piccolo e quando vale $np \approx \lambda$. Ovvero quando il numero delle prove è alto e la probabilità di successo molto bassa, infatti la _variabile di poisson_ è anche detta variabile _degli aventi rari_




#### Momenti e varianza
_sia_  $X$ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_  _di poison_ di parametro $\lambda$ non si può dire a priori se questo accetta _[[Variabili aleatoria - Momenti|momento primo]]_ ma essendo una variabile sempre positiva vale che $$\begin{array}{}
\displaystyle\mathbb{E}[X] & = &\displaystyle \sum^{+\infty}_{h=0}he^{-\lambda}\frac{\lambda^{h}}{h!} \\
 & = & \displaystyle\lambda e^{-\lambda}\sum^{+\infty}_{h=1}\frac{\lambda^{h-1}}{(h-1)!} &  \\ & 
= & \displaystyle\lambda e^{-\lambda}\sum^{+\infty}_{k=0}\frac{\lambda^{k}}{k!} & = & \lambda
\end{array}$$ e con conti simili si ottiene [[Variabili aleatoria - Momenti|momento secondo]]   $$\mathbb{E}[X^{2}]=\lambda + \lambda^{2} $$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$Var(X)=\lambda+\lambda^{2}-\lambda^{2}=
\lambda$$
La  _[[Funzione generatrice di momenti (MTF)|funzione generatrice dei momenti]]_ di questa variabile è  $$M_{X}(t)=e^{\lambda(e^{t}-1)}$$


#### Proposizione
_siano_ $X$ e $Y$ sono  [[Variabili Aleatorie (Casuali)|variabili aleatorie]] _[[Variabili Aleatorie Notevoli - Poisson|Poisson]]_ di parametro $\lambda$ e $\lambda’$ 
_se_ sono _[[Indipendenza di Variabili aleatorie|indipendenti]]_ 
_allora_ la _variabile aleatoria_ $Z= X+Y$ è  di _poisson_ di parametro $\lambda + \lambda’$ 
