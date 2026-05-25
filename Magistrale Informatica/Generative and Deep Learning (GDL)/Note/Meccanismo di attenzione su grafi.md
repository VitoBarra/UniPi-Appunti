---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Meccanismo di attenzione su grafi
---

Il **Deep Learning for Graph** estende poi il message passing con l'attenzione. Se $\alpha_{vj}$ misura il peso assegnato dal nodo $v$ al vicino $j$, si scrive
$$
h_v^{(l)}=\sum_{j \in N(v)} \alpha_{vj}W h_j^{(l-1)}.
$$
Qui $W$ trasforma il messaggio del vicino e $\alpha_{vj}$ ne controlla la rilevanza; operativamente, il nodo costruisce un'aggregazione pesata adattiva del vicinato. Le versioni multi-head ripetono l'operazione in piu sottospazi e permettono pesature differenti sullo stesso intorno, in analogia con il [[Meccanismo Self-Attention|meccanismo di self-attention]]. Questa famiglia e trattata piu direttamente in [[Graph Attention Network]]. ![[IMG - graph self-attension.png]]
![[IMG - Deep GraphNetworks architettura completa.png]]
