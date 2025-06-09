---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Bernulli
---
Consideriamo il caso in cui vogliamo trovate la _[[Legge di Probabilita|legge di probabilità]]_  della situazione in cui ci interessano solo _due esiti_ di una prova sola prova 
chiamiamo solo una due due esiti “_successo_”  e questa ha [[Definizione di Probabilità|probabilita]] $p\in (0,1)$

#### Variabile di Bernulli (Definizione)
è una [[Variabili Aleatorie Notevoli - Binomiale|variabile binomiale]] con $n=1$ e indicata con $B(p)$ ed è quindi espressa da $$\begin{array}{}
\mathcal{P}\{X=1 \} & = & p \\
\mathcal{P}\{X=0  \} & = & q & = &  1-p
\end{array}$$
#### Calcolo dei momenti e varianza
[[Variabili Aleatorie Notevoli - Bernulli|la variabile di Bernoulli]] assume il valore 1 con [[Definizione di Probabilità|probabilità]] $p$ ed il valore $0$ con [[Definizione di Probabilità|probabilita]] $(1−p)$, ed è dunque immediato constatare i [[Variabili aleatoria - Momenti|momenti]] _primo e secondo_ siano $$E[X]=p \ \ \ \ \ \ \ E[X^{2}] =p$$
 e quindi la [[Variabili aleatorie - Varianza|varianza]] risulta $$Var(X) =p−p^{2}=p(1−p)$$
 e la [[Funzione generatrice di momenti (MTF)|Funzione generatrice di momenti]] risulta essere $$M_{X}(t)=pe^{t}+1-p$$