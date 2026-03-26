---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Esponenziale
---
la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ **esponenziale** ha [[Legge di Probabilita|legge di probabilità]] definita dalla **densità esponenziale** di parametro $\lambda>0$ e questa è definita come  
$$f(x)=\begin{cases}
\lambda e^{-\lambda x} & x>0 \\
0 & x\le 0
\end{cases}$$

Si verifica che questa funzione è effettivamente una [[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densità di probabilità]] poiché
$$\left.\int_{0}^{+\infty}\lambda e^{-\lambda x}\,dx=-e^{-\lambda x}\right|_{0}^{+\infty}=1.$$

Poiché la densità è diversa da $0$ solo per $x>0$, si ha $\mathcal{P}(X\le0)=0$.

Questa distribuzione si usa per modellare **tempi di attesa tra eventi aleatori indipendenti** che avvengono con **tasso medio costante** $\lambda$. In questo contesto $\lambda$ rappresenta il **numero medio di eventi per unità di tempo**.  

Se gli eventi si verificano con un ritmo costante e indipendente dal passato (come negli arrivi di clienti in una coda, nei decadimenti radioattivi o nei guasti di componenti elettronici), il tempo che intercorre tra due eventi consecutivi segue una distribuzione esponenziale. Questo avviene perché la probabilità che l'evento avvenga in un piccolo intervallo di tempo dipende solo dalla lunghezza dell'intervallo e non da quanto tempo è già trascorso.

Formalmente, la distribuzione esponenziale è l'unica distribuzione continua che possiede la proprietà _[[Variabili aleatorie senza memoria|senza memoria]]_, cioè$$\mathcal{P}(X>s+t\mid X>s)=\mathcal{P}(X>t)$$Questa proprietà esprime il fatto che, se si è già atteso un tempo $s$ senza che l'evento si sia verificato, il tempo di attesa rimanente ha la stessa distribuzione di $X$.

### Funzione di ripartizione

La [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] di $X$ è
$$F(x)=\mathcal{P}(X\le x).$$

Per $x<0$ vale immediatamente
$$F(x)=0$$
poiché la variabile può assumere solo valori positivi.

Per $x\ge0$ si calcola integrando la densità
$$F(x)=\int_{0}^{x}\lambda e^{-\lambda t}\,dt$$
da cui
$$F(x)=1-e^{-\lambda x}.$$

Quindi
$$F(x)=\begin{cases}
1-e^{-\lambda x} & x\ge0 \\
0 & x<0
\end{cases}.$$
La probabilità che il tempo di attesa sia **maggiore di $x$** è quindi
$$\mathcal{P}(X>x)=1-F(x)=e^{-\lambda x},$$
che rappresenta la **funzione di sopravvivenza** della distribuzione esponenziale.



mentre la sua inversa  $F^{-1}(x)$ si ottiene come:
$$F(x)=1-e^{-\lambda x}$$
$$1-F(x)=e^{-\lambda x}$$
$$\ln(1-F(x))=-\lambda x$$
$$x=-\frac{1}{\lambda}\ln(1-F(x)).$$


#### Momenti e varianza
_sia_  $X$ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ _esponenziale_ di parametro $\lambda$ non si può dire a priori se questo accetta _[[Variabili aleatoria - Valore atteso|momento primo]]_ ma essendo una variabile positiva per $x$ _positivo_ vale che  $$\begin{array}{}
\displaystyle\mathbb{E}[X] & = &\displaystyle \int ^{+\infty}_{0}\lambda xe^{-\lambda x} \, dx  \\
& = & \displaystyle\frac{1}{\lambda}\int ^{+\infty}_{0}te^{-t} \, dt  
& =  &\displaystyle \frac{1}{\lambda}
\end{array}$$ e con conti simili si ottiene [[Variabili aleatoria - Valore atteso|momento secondo]]   $$\mathbb{E}[X^{2}]=\frac{2}{\lambda^{2}} $$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]]  $$Var(X)=\frac{2}{\lambda^{2}}-\left( \frac{1}{\lambda} \right)^{2}=\frac{1}{\lambda^{2}}
$$
e la funzione di [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] è $$M_{x}(t)=\left( 1-\frac{t}{\lambda} \right)^{-1}$$


### Composizioni notevoli

_siano_ $X_1,\dots,X_n$ [[Variabili Aleatorie (Casuali)|variabili aleatorie]] [[Indipendenza Stocastica|indipendenti]] con distribuzione **esponenziale** di parametri $\lambda_1,\dots,\lambda_n$.  
_definiamo_ $$X=\min(X_1,\dots,X_n)$$Allora $X$ è ancora una **Distribuzione esponenziale** con parametro$\lambda=\lambda_1+\dots+\lambda_n$

Il risultato si ottiene osservando che$$\mathcal{P}(X>t)=\mathcal{P}(X_1>t,\dots,X_n>t)$$Poiché le variabili sono indipendenti vale che: $$\mathcal{P}(X>t)=\prod_{i=1}^n \mathcal{P}(X_i>t)$$Per una variabile esponenziale vale $\mathcal{P}(X_i>t)=e^{-\lambda_i t}$, quindi$$
\mathcal{P}(X>t)=\prod_{i=1}^n e^{-\lambda_i t}
= e^{-(\lambda_1+\dots+\lambda_n)t}
$$
Questa è la funzione di sopravvivenza di una distribuzione esponenziale di parametro $\lambda_1+\dots+\lambda_n$, da cui segue la tesi.

Questo risultato ha un'interpretazione naturale nei modelli di **tempo di attesa tra eventi indipendenti**: se più eventi possono verificarsi indipendentemente con tassi $\lambda_1,\dots,\lambda_n$, il tempo fino al **primo evento tra tutti** è esponenziale con parametro pari alla somma dei tassi.