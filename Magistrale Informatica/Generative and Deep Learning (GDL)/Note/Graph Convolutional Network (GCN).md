---
Course: "[[Machine Learning (ML)]]"
tags:
  - GDL
  - IIA
  - ML
Area:
topic:
SubTopic:
---

# Graph Convolutional Network (GCN)
---
un modo per allenare reti neurali per grafi è costruire iterativamente una rete sfruttando il meccanismo di passaggio di messaggi.
arche

![[IMG - immagini come grafi.png]]
l algoritmo graph 4 neural network ad ogni iterazione si aggiunge un layer è il campo recettivo è incrementalmente esteso in funzione della profondità.
![[IMG - GCN radius.png]]
e calcola una singola variabile di stato per ogni layer e per ogni layer che vengono poi  combinate in un neurone di output. 
![[IMG - GCN Percettiva Radius.png]]
Formalmente può essere descritto da 

$$
\mathbf{h}_v^{(l)} = 
\begin{cases}  

\displaystyle h_v^{(1)}=\left( \sum^{l^v}_{j=0}w_{1_j}L_j(v) \right) \\
\displaystyle h_v^{(l)}=f\left( \sum^{L^v}_{j=0}w_{l_j}L_j(v)+\sum^{l-1}_{j=1}\hat{w}_{j_j}\sum_{u \in  N(v)}h_u^{(j)} \right)
\end{cases}$$








## Readout e pooling
Il **Deep Learning for Graph** richiede infine un passaggio da embedding locali a embedding globali. Quando il task e di livello grafo, si definisce un **readout** permutation invariant che aggrega gli embedding nodali in un singolo embedding di grafo, cioe un [[Graph-level Readout|readout di livello grafo]]; il pooling introduce invece una gerarchia, contraendo gruppi di nodi in super-nodi e accorciando le distanze di propagazione. Operativamente, il readout costruisce una rappresentazione globale, mentre il pooling aumenta astrazione e trasferimento dell'informazione, ma nei task nodali va usato con cautela perche eliminare nodi significa eliminare target di predizione.
![[IMG - Graph embedding.png]]
![[IMG - Poolign on graph.png]]
