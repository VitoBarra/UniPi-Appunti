---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Attention on graphs
---

# Graph Attention Network
La **Graph Attention Network** introduce un meccanismo di attenzione nel [[Message Passing Neural Network (MPNN)|message passing]] su grafi, cosi che i contributi dei vicini non vengano trattati tutti con lo stesso peso. L'idea e sostituire un'aggregazione uniforme con una pesatura adattiva che dipende dal contenuto dei nodi coinvolti nella relazione.

Si definisce per ogni coppia $(v,j)$, dove $v$ e il nodo che aggiorna il proprio stato e $j \in N(v)$ un nodo vicino, un coefficiente di attenzione $\alpha_{vj}$. Se $W$ e la trasformazione applicata al messaggio del vicino e $h_j^{(l-1)}$ e il suo embedding al layer precedente, l'aggiornamento si scrive
$$
h_v^{(l)}=\sum_{j \in N(v)}\alpha_{vj}Wh_j^{(l-1)}.
$$
La formula rappresenta un'aggregazione pesata del vicinato; operativamente, il nodo puo enfatizzare vicini piu rilevanti e attenuare quelli meno utili per il task.

I coefficienti $\alpha_{vj}$ si ottengono tipicamente normalizzando punteggi di compatibilita tramite softmax. In questo senso la Graph Attention Network trasferisce sui grafi il principio del [[Meccanismo Self-Attention|self-attention]], ma in forma locale: ogni nodo non guarda tutti gli altri nodi del grafo, bensi il proprio vicinato strutturale.

Le versioni multi-head replicano il meccanismo in piu sottospazi e combinano piu pesature dello stesso intorno. Questo aumenta la flessibilita del modello, ma non elimina i limiti strutturali del message passing locale, come difficolta sulle dipendenze molto lunghe o in grafi fortemente eterofili.

Proprieta chiave:
- introducono attenzione locale nel message passing
- pesano in modo adattivo i contributi dei vicini
- sono l'analogo grafico del self-attention locale
- multi-head attention aumenta la flessibilita dell'aggregazione
