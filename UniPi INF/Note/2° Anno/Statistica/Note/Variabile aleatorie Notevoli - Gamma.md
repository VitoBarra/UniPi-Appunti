---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabile aleatorie Notevoli - Gamma
---


#### Densità Gamma (Definizione)
Si chiama _densita gamma_ di parametri $r,\lambda>0$ indicata con $\Gamma(r,\lambda)$ la funzione definita come $$f(x)=\begin{cases}
\frac{1}{\Gamma(r)}\lambda^{r}x^{r-1}e^{-\lambda x} & x>0 \\
0 & x\leq 0
\end{cases}$$e questa è effettivamente una [[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densità]] siccome vale $$\int ^{+\infty}_{0}(\lambda x)^{r-1}e^{-\lambda x}\lambda \, dx = \int^{+\infty}_{0}t^{r-1}e^{-t}  \, dt=\Gamma(r) $$ con $t=(x\lambda)$. 
>[!tip]
> la [[Variabili Aleatorie Notevoli - Esponenziale|densita esponenziale]] corrisponde alla _densita gamma_ $\Gamma(1,\lambda)$


#### Momenti e varianza
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variaible aleatoria]] con [[Probabilita sui numeri Reali|densita]] $\Gamma(r,\lambda)$ 
_allora_ questa ha tutti i [[Variabili aleatoria - Momenti|momenti]] e $\forall \beta>0$ vale $$\mathbb{E}\left[ X^{\beta}\right]= \frac{\Gamma(r+\beta)}{\Gamma(r)\lambda^{\beta}}$$ in particolare vale che i _momenti primi e secondi siano_$$
\begin{array}
\mathbb{E}[X] & = & \cfrac{\Gamma(r+1)}{\Gamma(r)\lambda} & = & \cfrac{r}{\lambda}  \\
\mathbb{E}[X^{2}]  & = &  \cfrac{\Gamma(r+2)}{\Gamma(r)\lambda} & = & \cfrac{(r+1)r}{\lambda} \\
\end{array}
$$e di conseguenza la [[Variabili aleatorie - Varianza|varianza]] risulta
$$Var(X)= \cfrac{r}{\lambda^{2}}$$
_Dimostrazione_
	Poiché $X$ prende valori positivi vale $$\begin{array}
\mathbb{E}\left[ X^{\beta} \right] &  = \\
\displaystyle\cfrac{1}{\Gamma(r)}\int ^{+\infty}_{0}x^{\beta}\lambda^{r}x^{r-1}e^{-\lambda x}  \, dx  & =  \\
\displaystyle\cfrac{1}{\Gamma(r)\lambda^{\beta}}\int ^{+\infty}_{0}\lambda^{r+\beta}x^{r+\beta-1}e^{-\lambda x} \, dx  & = \\
\displaystyle\cfrac{\Gamma(r+\beta)}{\Gamma(r)\lambda^{\beta}} 
	\end{array}$$ che dimostra che esistono tutti i [[Variabili aleatoria - Momenti|momenti]] e non abbiamo mai dovuto calcolare esplicitamente $\Gamma(r)$ ma abbiamo usato l eguaglianza $\Gamma(r)=(r-1)\Gamma(r-1)$

e la _[[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]]_ risulta essere $$M_{X}(t)=\left[ \frac{1}{1-\lambda t} \right]^{r}$$ 


#### Proposizione
_siano_ $X,Y$ due [[Variabili Aleatorie (Casuali)|variabili aleatorie]] con densita $\Gamma_{X}(r,\lambda)$ e $\Gamma_{Y}(s,\gamma)$
_se_ queste sono [[Indipendenza di Variabili aleatorie|indipendenti]]
_allora_ la variabile $Z=X+Y$ ha [[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita]] $$Z \sim\Gamma(r+s,\lambda)$$

_Dimostrazione_
	_sia_ $Z=X+Y$ e usando la [[Formule della convoluzione#Formule della convoluzione|formula della convoluzione]] otteniamo $$\begin{array}{}
\displaystyle f_{Z}(z) & = & \displaystyle\frac{\lambda^{r+s}e^{-\lambda z}}{\Gamma(r)\Gamma(s)} \int^{z}_{0} x^{r-1}(z-x)^{s-1} \, dx    \\ & = & \displaystyle
\frac{\lambda^{r+s}z^{r+s-1}e^{-\lambda z}}{\Gamma(r)\Gamma(s) }\int^1_0 y^{r-1}(1-y)^{s-1} \, dy 
\end{array}$$in cui il primo passo e la sostituzione della definizione _densita gamma_ nella _formula do convoluzione_ e il secondo segue dalla sostituzione $x=zy$
	l integrale di desta è chiamato _funzione $\beta$_ di parametri $r,s$ e vale $$\begin{array}{}
\Gamma(r)\Gamma (s) & = \\
\displaystyle\left( \int^\infty_0 x^{r-1}e^{-x} \, dx  \right) \left( \int^{\infty}_{0}y^{s-1}e^{-y}  \, dx  \right)  & =  \\
\displaystyle \int^\infty_0  \int^\infty_0 x^{r-1}y^{s-1}e^{-x-y}   \, dx  \, dy  & = \\ \displaystyle
\int^\infty_0  \int^1_0 e^{-a}(ab)^{r-1}a^{s-1}(1-b)^{s-1}a  \ \ \, da  \, db   & = \\
\displaystyle\Gamma(r+s)\int^1_0 b^{r-1}(1-b)^{s-1} \, db 
\end{array}$$dove al terzo passaggio si è usata la sostituzione $(x,y)=(ab,a(1-b))$. da qui dividendo per $\Gamma(r)\Gamma(s)$ si ottiene la tesi.



