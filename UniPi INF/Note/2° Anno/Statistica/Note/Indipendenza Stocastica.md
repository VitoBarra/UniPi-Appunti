---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Indipendenza Stocastica
---
Presi due eventi $A$ e $B$ _[[Probabilita|trascurabili]]_ si vogliono studiare i casi in cui _conoscere_ la realizzazione di uno dei due _eventi_ non cambia la conoscenza della probabilita del altro.
Abbiamo che quindi deve valere che$\mathcal{P}(A)=\mathcal{P}(A|B)$ e $\mathcal{P}(B)=\mathcal{P}(B|A)$ e applicando la definizione di [[Probabilita condizionata|Probabilita condizionata]] otteniamo che $$
\begin{array}
\mathcal{P}(A) & = & \cfrac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)} \\
\mathcal{P}(A \cap B) & = & \mathcal{P}(A)\mathcal{P}(B)
\end{array}
$$ e vale per entrambi. E questo ha senso anche se i due eventi sono _trascurabili_  

#### Indipendenza stocastica (definizione)
_siano_ $A$ e $B$ due _eventi_  questi sono detti _indipendenti_ (stocasticamente) se vale che $$
\mathbf{P}(A\cap B) =\mathbf{P}(A) \times\mathbf{P}(B)
$$
e valgono i seguenti fatti
- se $A$ e $B$ sono _indipendenti_, sono _indipendenti_ anche $A^c$ e $B$, $A$  e $B^c$, $A^c$ e $B^c$
- se $\mathcal{P}(A) =0$ oppure $\mathcal{P}(A) = 1$, $A$ è sempre _indipendente_ da _qualsiasi altro evento_
- due eventi _incompatibili_ (cioè che hanno intersezione vuota) non possono essere indipendenti, a meno che uno dei due sia trascurabile.

#### Indipendenza di più eventi
_siano_ $n$  _eventi_ $A_1,\dots,A_n$, questi si dicono _indipendenti_ se per ogni intero $k \in [2, n]$ e per ogni scelta di $1 \leq i_1 < \dots < i_k \leq n$  , vale l’eguaglianza

$$
\mathbf{P}(A_{i_1} \cap \cdots \cap A_{i_k}) = \mathbf{P}(A_{i_1}) \dots \mathbf{P}(A_{i_k})
$$
e per ogni $n$ vanno verificate $2^{n}-n-1$ 