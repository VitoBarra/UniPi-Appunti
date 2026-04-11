---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Flusso su grafo
---
Un **Flusso su grafo** è definito come 
Sia $G=(N,A)$ un [[Graph Theory|grafo]] orientato. Un **flusso su grafo** e una funzione che associa ad ogni arco $(i,j) \in A$ una quantita $x_{ij}$, interpretabile come quantita di flusso che attraversa l'arco $(i,j)$.
Nel caso classico del [[Problema del flusso massimo]], il flusso deve soddisfare:
- i **vincoli di capacita**: $0 \leq x_{ij} \leq u_{ij}$ per ogni arco $(i,j) \in A$
- i **vincoli di conservazione**: per ogni nodo interno, il flusso entrante e uguale al flusso uscente
Se sono fissati un nodo sorgente $s$ e un nodo pozzo $t$, il **valore del flusso** e la quantita totale uscente da $s$, equivalente alla quantita totale entrante in $t$.

### Osservazioni
- nei [[Problema del cammini minimi|problemi di cammino minimo]] le variabili possono essere interpretate come flussi sugli archi
- nel [[Problema del flusso di costo minimo]] al flusso e associato anche un costo per ogni arco
