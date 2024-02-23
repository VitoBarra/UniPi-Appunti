---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Geometrica
---
Consideriamo il caso in cui vogliamo trovate la _[[Probabilita sui numeri Reali|legge di probabilità]]_  della situazione in cui ci interessano solo _due esiti_ di una prova ripetuta $n$ volte 
chiamiamo solo una due due esiti “_successo_”  e questo ha [[Definizione di Probabilita|probabilità]] $p\in (0,1)$

#### Variabili geometriche (Definizione)
_sia_ $X$ la _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ tale che $X=h$ indica  con quale probabilità abbiamo il _primo successo_ al tentativo $h$ 
_allora_ questa è scritta come$$\mathcal{P}\{ X=h \} = (1-p)^{h-1}p \ \ \ \ \ \ \ \ h \in  \mathbb{N}^{+}$$
infatti dati gli eventi $A_{i}$ che indica il successo alla prova $i$-esima$$ \begin{array}
\mathcal{P}(X=h) & = & \mathcal{P}(A_{1}^{c}\cap A_{2}^{c}\cap \dots \cap A_{h}) & = \\
\mathcal{P}(A_{1}^{c})\mathcal{P}(A_{2}^{c})\dots \mathcal{P}(A_{h}) & = & (1-p)^{h-1}p
\end{array}
$$
##### Memoria della variabile (Teoria)
La variabile _aleatoria geometrica_ ha la proprietà di essere _senza memoria_ ovvero $$\mathcal{P}\{X=n+h\mid X>n\}=\mathcal{P}\{X=h\}$$dove il $|$ è la [[Probabilita condizionata|probabilita condizionata]]



#### Momenti  e varianza
_sia_ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ $X$ una _variabile geometrica_ allora abbiamo che i momenti primo e secondo siano
$$\begin{array}{}
\mathbb{E}[X] & = & \cfrac{1}{p} \\
\mathbb{E}[X^{2}] & =
\end{array}$$ e di conseguenza la [[Variabili aleatorie - Varianza|varianza]] risulta $$Var(X)=\frac{1-p}{p^{2}}$$
e la sua [[Funzione generatrice di momenti (MTF)|funzione generatrice di momenti]] risulta $$M_{X}(t)=\frac{pe^{t}}{1-e^{t}(1-p)}$$ 