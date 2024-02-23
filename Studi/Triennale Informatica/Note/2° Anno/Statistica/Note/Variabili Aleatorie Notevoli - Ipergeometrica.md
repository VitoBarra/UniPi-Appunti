---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Ipergeometrica
---
Consideriamo il caso in cui vogliamo trovate la _[[Probabilita sui numeri Reali|legge di probabilità]]_  della situazione in cui ci interessano solo _due esiti_ di una prova ripetuta $n$ volte _senza rimpiazzo_,
chiamiamo solo una due due esiti “_successo_”  e questa ha [[Definizione di Probabilita|probabilita]] $p\in (0,1)$ essendo _senza rimpiazzo_ $p$  varia ad ogni estrazione.

>[!tip]
>lo stesso caso _con rimpiazzo_ è modellato con la variabile [[Variabili Aleatorie Notevoli - Binomiale|binomiale]] 
#### Variabile Ipergeometrica (Definizione)
_sia_ $X:\Omega \rightarrow\{ 1,\dots,n\}$ la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ che _conta_ il numero di _successi_ __senza rimpiazzo__
- $A$ un [[Insiemi Matematici|insieme]] con $|A|=n$ l insieme degli  _elementi totali_ da cui estrarre
- $B \subseteq A$ un [[Insiemi Matematici|sotto insieme]] con $|B|=k$  l insieme degli elementi considerati _successi_  
- $r$ il numero di _estrazioni_ 
_se_ vale che $$\mathcal{P}(X=h)=\frac{\begin{pmatrix}k \\ h\end{pmatrix}\begin{pmatrix}n-k \\ r-h\end{pmatrix}}{\begin{pmatrix}n \\ r\end{pmatrix}}$$
_allora_ è detta _variabilie ipergeometrica_ di parametri $n,k,r$ indicata con $\mathcal{H}(n,k,r)$ 
dove
- $\begin{pmatrix}k \\ h\end{pmatrix}$ è il numero di possibili modi di estrarre $h$ _elementi_ tra i $k$ elementi di $B$ 
- $\begin{pmatrix}n-k \\ r-h\end{pmatrix}$ è il numero di possibili _estrazioni_ dei restanti $r-h$ elementi tra gli $n-k$ elementi _non in_ $B$
- $\begin{pmatrix}n \\ r\end{pmatrix}$ è il numero di possibili estrazioni di $r$ elementi dal insieme $A$

