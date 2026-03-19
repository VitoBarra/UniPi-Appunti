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
Le **misure di centralità** quantificano l'importanza topologica dei nodi nella rete e poiché un nodo può essere importante per ragioni diverse, si usano [[Network science - Misure di centralita|misure differenti]]. 

