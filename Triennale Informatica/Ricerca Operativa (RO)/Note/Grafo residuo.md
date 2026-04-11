---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Grafo residuo
---
Dato un [[Flusso su grafo|flusso]] ammissibile $x$ su un [[Graph Theory|grafo]] $G=(N,A)$, il **grafo residuo** relativo ad $x$ è il grafo $G(x)=(N,A(x))$ avente gli stessi nodi del grafo $G$.

Gli archi del grafo residuo e le corrispondenti capacità residue sono definiti come segue:
- se $(i,j) \in A$ con $x_{ij} < u_{ij}$, allora $(i,j) \in A(x)$ con capacità residua $r_{ij} = u_{ij} - x_{ij}$
- se $(i,j) \in A$ con $x_{ij} > 0$, allora $(j,i) \in A(x)$ con capacità residua $r_{ji} = x_{ij}$

Se agli archi sono associati anche dei costi, allora nel [[Grafo residuo|grafo residuo]] i costi vanno ricalcolati cosi:
- se $(i,j) \in A$ con $x_{ij} < u_{ij}$, allora l'arco residuo in avanti $(i,j)$ ha costo $c'_{ij} = c_{ij}$
- se $(i,j) \in A$ con $x_{ij} > 0$, allora l'arco residuo all'indietro $(j,i)$ ha costo $c'_{ji} = -c_{ij}$

Il [[Grafo residuo]] descrive tutta la possibilità residua di modificare il flusso corrente:
- gli archi in avanti rappresentano quanta ulteriore capacità è ancora disponibile
- gli archi all'indietro rappresentano quanta parte del flusso già inviato può essere annullata
