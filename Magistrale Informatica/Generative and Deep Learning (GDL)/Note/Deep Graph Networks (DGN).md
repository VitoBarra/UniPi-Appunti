---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Deep Graph Networks
---

# Deep Graph Networks (DGN)
Le **Deep Graph Networks (DGN)** sono una famiglia di modelli neurali per grafi che estende il [[Deep Learning|deep learning]] a domini non regolari mediante aggiornamenti locali ripetuti sugli stati nodali. L'idea centrale e che ogni nodo mantenga una rappresentazione latente che viene raffinata iterativamente usando il proprio contenuto, il contenuto dei vicini e la struttura degli archi.

![[IMG - Deep Graph Networks.png]]
Nel quadro generale delle DGN si definisce, per ogni nodo $v$ e layer $l$, uno stato latente $h_v^{(l)}$. Se $\mathcal{N}(v)$ indica il vicinato di $v$, $L_v$ l'informazione locale del nodo e $\mathbf{W}^{(l)}$ i parametri del layer, l'aggiornamento si scrive in forma astratta come
$$
h_v^{(l)}=AGG_{\mathbf{W}^{(l)}}\left(L_v,h_v^{(l-1)},\{h_u^{(l-1)}:u \in \mathcal{N}(v)\}\right).
$$
La formula rappresenta una propagazione locale di informazione; operativamente, ogni layer e un passo di contestualizzazione in cui il nodo incorpora informazione dal suo intorno.

Il cuore delle DGN e quindi il [[Message Passing Neural Network (MPNN)|message passing]]. Ogni nodo invia un messaggio, riceve i messaggi dai vicini, li aggrega con un operatore invariante alla permutazione e aggiorna il proprio embedding. Dopo pochi layer il modello codifica struttura locale, mentre aumentando la profondita cresce il **receptive field** e il nodo integra informazione da regioni sempre piu ampie del grafo.

Le DGN possono produrre output a diversi livelli. Se il task e nodale, l'output si ottiene direttamente dagli embedding $h_v^{(L)}$ dell'ultimo layer. Se il task e globale, si applica un [[Graph-level Readout|graph-level readout]] o un pooling che aggrega gli embedding nodali in una rappresentazione unica del grafo. Questa flessibilita rende le DGN il quadro piu generale entro cui si collocano [[Graph Convolutional Network (GCN)|GCN]], graph attention models, modelli ricorrenti su grafi e architetture ibride.

Proprieta chiave:
- le DGN definiscono un framework generale per neurali su grafi
- il loro operatore fondamentale e l'aggiornamento locale degli stati nodali
- il message passing e la realizzazione piu comune del framework
- output nodali e globali si ottengono cambiando il livello di readout









