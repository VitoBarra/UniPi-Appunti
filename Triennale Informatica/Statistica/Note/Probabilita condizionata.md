---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Probabilità condizionata
---
preso uno _[[Definizione di Probabilita#Probabilità assiomatica secondo Kolmogorov (definizione)|spazio delle probabilità]]_ $(\Omega,\mathcal{F},\mathcal{P})$ conoscendo l’esito di un evento $B$ _non trascurabile_ si possono fare delle considerazioni su un _altro evento_ $A$ anche esse non trascurabile modificandone cosi la _[[Definizione di Probabilita|Definizione di Probabilita]]_
infatti abbiamo che la _Probabilità Condizionata_ di $A$ rispetto a $B$ è definita come$$
\mathcal{P}(A\mid B) = \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}
$$ da cui deriva la **regola del prodotto** $$
 \mathcal{P}(A \cap B) = \mathcal{P}(A\mid B)\mathcal{P}(B)
 =\mathcal{P}(B\mid A)\mathcal{P}(A)$$
dove la seconda eguaglianza viene dal fatto che$$
\begin{array}
\mathcal{P}(A \mid B)  & = &\displaystyle  \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}  & \implies &  \mathcal{P}(A \mid B)\,\mathcal{P}(B)  & = &  \mathcal{P}(A \cap B) \\
\mathcal{P}(B \mid A)  & = &\displaystyle  \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(A)}  & \implies &  \mathcal{P}(B \mid A)\,\mathcal{P}(A)  & = &  \mathcal{P}(A \cap B) 
\end{array}
$$e quindi vale che:$$
\boxed{\mathcal{P}(A \mid B)\,\mathcal{P}(B) = \mathcal{P}(B \mid A)\,\mathcal{P}(A)}
$$

In _generale_ vale che presi  $A_1,\dots,A_n$ ovvero per $n$ _eventi_  e supponendo che $A_1 \cap\dots \cap A_{n-1}$ si  un evento non trascurabile allora$$
\mathcal{P}(A_1 \cap\dots \cap A_n) = \mathcal{P}(A_1)\mathcal{P}(A_2|A_1) \dots\mathcal{P}(A_n|A_1 \cap\dots \cap A_{n-1})
$$ questa è chiamata **_formula del condizionamento ripetuto_**
la _dimostrazione_ di questo è immediata e basta sostituire ogni termine con la definizione di _probabilità condizionata_ 

>[!tip]
>per $A_{1} \cap\dots\cap A_{k}$ per $k\in[1,n-1)$ l _evento_ non è trascurabile

