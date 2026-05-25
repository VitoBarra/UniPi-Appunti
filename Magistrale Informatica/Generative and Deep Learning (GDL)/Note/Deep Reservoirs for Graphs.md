---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Reservoir graph models
---

# Deep Reservoirs for Graphs
I **Deep Reservoirs for Graphs** estendono il [[RandRNN - Reservoir Computing|reservoir computing]] al dominio dei grafi mantenendo l'idea che la dinamica interna non venga addestrata end-to-end. Invece di ottimizzare tutti i pesi della rete, si fissano piu strati ricorrenti o contestuali inizializzati casualmente e si addestra soprattutto il readout finale.

Il principio e che ogni layer di reservoir trasformi gli embedding nodali in nuove rappresentazioni contestuali, lasciando invariata la dinamica interna del blocco. Se $h_v^{(l)}$ indica lo stato del nodo $v$ al layer $l$, la propagazione resta una funzione del contenuto del nodo e degli stati dei vicini, ma i parametri principali del reservoir sono congelati. Operativamente, la profondita introduce raffinamento gerarchico senza imporre il costo di un addestramento completo dei pesi ricorrenti.

L'idea si collega direttamente alla [[Graph Echo State Network]], che ne rappresenta la formulazione piu elementare con un singolo reservoir o con una dinamica limitata. Nei deep reservoirs si impilano piu trasformazioni, ottenendo una rappresentazione piu ricca del grafo pur mantenendo il vantaggio computazionale di addestrare soprattutto il readout.

Il punto di forza del modello e l'efficienza: meno parametri da addestrare, minore rischio di instabilita ricorrente, tempi di training piu contenuti. Il limite e che la qualita della rappresentazione dipende molto dalla dinamica casuale fissata inizialmente, quindi l'adattamento al task e meno flessibile rispetto a GNN pienamente addestrate.

Proprieta chiave:
- estendono il reservoir computing a piu livelli su grafi
- mantengono fissi i reservoir e addestrano soprattutto il readout
- migliorano l'efficienza rispetto a modelli ricorrenti end-to-end
- sacrificano parte dell'adattivita per guadagnare stabilita e velocita


## Varianti globali
Il **Deep Learning for Graph** mantiene anche una linea ricorrente tramite i [[Deep Reservoirs for Graphs]], che fissano casualmente i pesi ricorrenti sotto vincoli di contrattivita e addestrano solo il readout. Operativamente, si conserva una dinamica contestuale stabile riducendo il costo di training, al prezzo di una minore adattivita interna, in continuita con [[RandRNN - Reservoir Computing|reservoir computing]], [[Reservoir Computing - Echo State Network (ESN)|echo state network]] e con il modello [[Graph Echo State Network]]. ![[IMG - Deep Reservoirs for Graphs.png]]
