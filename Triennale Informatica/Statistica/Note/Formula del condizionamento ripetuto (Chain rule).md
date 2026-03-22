---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Formula del condizionamento ripetuto (Chain rule)
---
La **formula del condizionamento ripetuto**, o **chain rule**, generalizza la [[Regola del prodotto|regola del prodotto]] a un numero arbitrario di eventi e deriva quindi da [[Probabilita condizionata|probabilita condizionata]]. Per eventi $A_1,\dots,A_n$, supponendo che ogni intersezione parziale $A_1\cap\dots\cap A_k$ con $k=1,\dots,n-1$ sia non trascurabile, vale $$\mathcal{P}(A_1\cap\dots\cap A_n)=\mathcal{P}(A_1)\mathcal{P}(A_2\mid A_1)\dots\mathcal{P}(A_n\mid A_1\cap\dots\cap A_{n-1})$$che in  forma compatta si puo scrivere anche$$\mathcal{P}\left(\bigcap_{i=1}^n A_i\right)=\prod_{i=1}^n \mathcal{P}\left(A_i\mid \bigcap_{j=1}^{i-1}A_j\right)$$ dove per $i=1$ si intende semplicemente $\mathcal{P}(A_1)$.

>[!tip]
>Per ogni $k\in\{1,\dots,n-1\}$ l'evento $A_1\cap\dots\cap A_k$ deve essere non trascurabile.

Questa stessa identita si applica anche alle [[Variabili Aleatorie (Casuali)|variabili aleatorie]] 