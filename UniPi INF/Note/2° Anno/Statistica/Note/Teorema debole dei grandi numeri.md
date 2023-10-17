---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Teorema debole dei grandi numeri
---
_sia_ $X_{1},X_{2},\dots$ una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|i.d.d]] dotate di [[Variabili aleatoria - Momenti|momento secondo]] _finito_ e $\mu=\mathbb{E}[X_{i}]$ il loro valore atteso (media), 
_allora_ $\overline{X}_n$ [[Convergenza in probabilita|converge in probabilita]] a $\mu$ per $n \to \infty$ per ogni $\varepsilon>0$, ovvero _vale_ $$\lim_{ n \to \infty } \left(\left |\cfrac{X_{1}+\dots +X_{n}}{n}- \mu\right| > \varepsilon \right)=0$$ questo ci dice che la _[[Statistica descrittiva - Dati Numerici#Media (definizione)|media campionaria]]_ dei primi $n$ termini converge alla _media teorica_, ovvero alla _[[Statistica descrittiva - Dati Numerici#Media (definizione)|media empirica]]_  quella su tutta la _popolazione_

_Dimostrazone_
	 si ha $$\begin{array}{}
\mathbb{E}[\overline{X}_n] & = & \cfrac{\mathbb{E}[X_1]+\dots+\mathbb{E}[X_n]}{n}= \mu \\ \\
Var(\overline{X}_n) & = & \cfrac{Var(X_1)+\dots+Var(X_n)}{n} \\
 &   = & \cfrac{Var(X_{1})}{n} \xrightarrow{n \to \infty } 0
\end{array}$$dove si prende $X_{1}$ per convenzione siccome la [[Variabili aleatorie - Varianza|varianza]] è uguale $\forall i \ \ Var(X_{i})$   e quindi si puo raggruppare con $nVar(X_{i})$ con $i$ qualsiasi, si sceglie $1$ per convenzione


>[!note]
>in realtà le ipotesi possono essere rilassante
>basta che 
>- le variabili siano [[Variabili aleatorie - Covarianza e correlazione|scorrelate]] 
>- tutte abbiano [[Variabili aleatoria - Momenti|valore atteso]] $\mu$  
>- le [[Variabili aleatorie - Varianza|varianze]] siano equilibrate, ovvero $\exists C. \forall i \ Var (X_{i}) \leq C$

