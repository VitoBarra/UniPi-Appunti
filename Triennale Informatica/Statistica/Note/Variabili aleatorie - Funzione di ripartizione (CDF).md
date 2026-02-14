---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili aleatorie - Funzione di ripartizione (CDF)
---
la **Funzione di ripartizione o Cumulative Distribution Function (CDF)** è una [[Funzioni|funzione]] che, data una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X:\Omega \rightarrow \mathbb{R}$, consente di descrivere la sua _[[Definizione di Probabilita|distribuzione]]_ $\mathcal{P}_{X}$

_sia_ $X:\Omega \rightarrow \mathbb{R}$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] si chiama _funzione di ripartizione_ di $X$ la [[Funzioni|funzione]] $F_{X}: \mathbb{R} \rightarrow[0,1]$ definita come $$F_{X}(x)=\mathcal{P}(X \leq x)$$e le proprietà di questa funzione sono le seguenti
- $F_{X}$  non decrescente, ovvero se $x<y$ allora $F(x) \leq F(y)$
- vale$$\lim_{ x \to -\infty } F(x)=0 \ \ \ \ \ \ \ \ \ \ \lim_{ x \to +\infty }F_{X}(x)=1 $$
- $F$ è [[Continuità di una funzione|continua]] a _destra_, ovvero $\forall x \in \mathbb{R}$ vale $F(x_{n})\rightarrow F(x)$ per ogni successione $x_{n}\rightarrow x$ con $x_{n}\geq x$


#### Funzioni di ripartizione discreta
la _funzione di ripartizione_ $F_{X}$ di una [[Variabili Aleatorie (Casuali)|Variabile Aleatoria]] $X$ discreta che assume valori $x_1,x_{2}\dots$ è una funzione _costante a gradini_ $$F_{X}(t)= \sum_{x_{i}\leq t}p(x_{i})$$nella funzione c è un salto in corrispondenza di ogni punto $x$ tale che $\mathcal{P}\{ X=x \}>0$ e l _ampiezza_ del salto è la _[[Definizione di Probabilita|probabilita]]_ di quel punto.

Abbiamo quindi che $$\mathcal{P}\{ X=x\}=F_{X}(x)-F_{X-}(x)$$dove $F_{X-}=\lim_{ y \to x }F(y)$ si intende il _[[Limiti|limite]] sinistro_ di $F_{X}$ nel punto $x$ 


#### Funzione di ripartizione con densita
_la funzione di ripartizione_  $F_X$ di una _variabile aleatoria_ $X$ con _densita_ è la funzione $$F_{X}(x)=\int _{-\infty}^{x}f(t) \, dt$$ ed è ovviamente continua.

nei casi in cui $f$ si [[Continuità di una funzione|continua]] o continua _a tratti_ avremmo _equivalentemente_ che $F_{X}\in C^{1}$ ovvero è _continua_ in $\mathbb{R}$ e la sua [[Derivate|derivata]] è _continua_ abbiamo che $$f(x)=\frac{dF_{X}(x)}{dx}$$quindi $f$ può essere ottenuta [[Derivate|derivando]] $F_{X}$


>[!warning]
>non tutte variabili aleatoree con _funzione di ripartizione_ [[Continuità di una funzione|continua]] sono _variabili aleatorie con densita_


##### Proposizione
data una _funzione di ripartizione_ $F_{X}:\mathbb{R} \rightarrow [0,1]$ esiste una ad una sola _probabilta_ $\mathcal{P}$ sui sotto [[Insiemi Misurabili|insiemi misurabili]] di $\mathbb{R}$ tale che $F(t)=\mathcal{P}((-\infty,t])$ ovvero che $F_{X}$ sia la _funzione di ripartizione_ della variabile $X$ la cui legge di probabilita è $\mathcal{P}_{X}=\mathcal{P}$ 

La conseguenza di questo è che _se_ due _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ hanno la stessa _funzione di ripartizione_ _allora_ sono _equidistribuite_ ovvero hanno la stessa _legge di probabilità_ e questa è ricostruibile dalla _funzione di ripartizione_


#### Applicazioni  pratiche
_sia_ $F_{X}$ la _funzione di ripartizione_ della variabile aleatoria $X$ si puo ricavare la _probabilita_ che questa ricada in un dato intervallo $[a,b]$ calcolando $$\mathcal{P}\{a < X \leq b\}=F_{X}(b)-F_{X}(a)$$e questo si verifiche siccome vale che $\{ a <X\leq b \}= \{ X \leq b \}\backslash\{ X\leq a \}$. e questa formula è _estendibile_ ai casi in cui
- $a = -\infty$ ($\mathcal{P}\{ X \leq b \}$) 
- $b=+ \infty$ ($\mathcal{P}\{ X>a \}$) 
ponendo 
- $F_{X}(-\infty)=0$
- $F_{X}(+\infty)=1$ 



