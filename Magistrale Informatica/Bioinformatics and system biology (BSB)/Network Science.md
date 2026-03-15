---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Network science
---
La **network science** studia la **topologia e la dinamica di reti complesse**, estendendo i concetti della [[Graph Theory|Teoria dei Grafi]] a sistemi reali come [[Biological networks|reti biologiche]], sociali e tecnologiche.  
In una rete:
- i **nodi** rappresentano entità ([[Proteine|proteine]], geni, persone, dispositivi)
- gli **archi** rappresentano interazioni o relazioni tra tali entità
L’analisi delle reti si concentra su **proprietà globali della struttura**, come la distribuzione delle connessioni, l’importanza dei nodi, la presenza di moduli e la capacità del sistema di trasmettere informazione.

## Distribuzione del grado
La **distribuzione dei gradi** $P(k)$ descrive la probabilità che un nodo abbia grado $k$.
- nelle **reti casuali** la distribuzione segue una legge di tipo **[[Variabili Aleatorie Notevoli - Poisson|Poisson]]**
- nelle reti reali (biologiche e sociali) segue spesso una **[[Variabili Aleatorie Notevoli - Esponenziale|Power law]]** $$P(k)\sim k^{-\gamma}$$Queste reti sono dette **scale-free networks** e sono caratterizzate da:
- molti nodi con pochi collegamenti
- pochi nodi con grado molto elevato (**hub**)
Gli hub svolgono un ruolo critico nella **connettività globale**, nella **robustezza della rete** e nella **propagazione dei segnali** nei sistemi biologici.
![[IMG - Network Science Degree distribution.png]]

## Small-World property
la proprietà **small-world** (Watts–Strogatz) è una proprietà topologica dei [[Graph Theory|grafi]] dove vale che:
- **alto [[Graph Theory|clustering]] medio** $\langle C \rangle$: i vicini di un nodo tendono a essere connessi tra loro, indicando la presenza di moduli funzionali locali
- **bassa lunghezza media dei cammini** $\langle L \rangle$: la distanza media tra due nodi qualsiasi è molto piccola, permettendo una rapida trasmissione dell’informazione

## Centralità dei nodi
Le **misure di centralità** quantificano l’importanza topologica dei nodi nella rete.

##### Degree Centrality
La **degree centrality** misura il numero di connessioni dirette di un nodo:$$C_D(v)=k_v$$
- Identifica nodi altamente interattivi
- Non tiene conto della struttura **globale** della rete, un nodo potrebbe avere alta **degree centrality** ma essere isolato e ha quindi bassa influenza 

##### Closeness Centrality
La **closeness centrality** misura quanto **velocemente** un nodo può raggiungere tutti gli altri nodi della rete:$$C_C(v)=\frac{N-1}{\sum_u d(v,u)}$$dove $d(v,u)$ è la distanza minima tra i nodi. 
- Un nodo con alta closeness può **diffondere rapidamente informazione o segnali** nella rete.

##### Betweenness Centrality
La **betweenness centrality** misura quanto frequentemente un nodo appare nei cammini minimi tra altri nodi: $$C_B(v)=\sum_{s\neq v\neq t}\frac{\sigma_{st}(v)}{\sigma_{st}}$$dove:
- $\sigma_{st}$ è il numero di cammini minimi tra $s$ e $t$
- $\sigma_{st}(v)$ è il numero di tali cammini che passano per $v$.
Un nodo può avere **grado basso ma betweenness elevata** se funge da **ponte tra moduli funzionali**, agendo da **botleneck**.

##### Eigenvector Centrality
L’**eigenvector centrality** assegna importanza ai nodi connessi ad altri nodi **importanti**.
Se $x_i$ è l’importanza del nodo $i$:$$Ax=\lambda x$$dove $A$ è la matrice di adiacenza e $x$ l’autovettore principale.

Una variante più robusta è il **PageRank**, che introduce un fattore di teletrasporto e può essere interpretato come un **random walk con restart**.