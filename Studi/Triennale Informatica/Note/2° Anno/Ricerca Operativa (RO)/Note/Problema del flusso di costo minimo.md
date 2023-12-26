---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Problema 
---

Prev: [[Ricerca Operativa (RO)]]

# Problema del flusso di costo minimo
---


# Modello

### Variabili decisionali

su un [[Grafo struttura dati|grafo]]  $G(N,A)$ per ogni arco $(i,j) \in A$ definiamo $x_{ij}$= flusso sul arco $(i,j)$

$$
\begin{cases}
\ \ \ \ \ \ \ \min \sum\limits_{(i,j)\in A} c_{ij}x_{ij} \\
\sum\limits_{(i,k)\in A} x_{ik}- \sum\limits_{(k,j)\in A} x_{kj} = b_k\ \ \ \ \ \ \ \ \forall k \in N\\
\ \ \ \ \ \ \ 0 \leq x_{ij} \leq u_{ij} \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \forall (i,j) \in A
\end{cases}
$$

### Esistenza di soluzione

per determinare se esistono soluzioni ammissibili per il problema del flusso di costo minimo su un grafo $G(N,A)$, si può risolvere il problema del flusso massimo sul grafo $G'(N',A')$, dove

- $N'= N \cup\{s,t\}$
- $A'=A \cup \{(s,i)\ |\ i\in N \ \ tale \ che \ b_i <0 \} \cup \{(j,t) \ | \ j \in N \ tale \ che\ b_i>0\}$
- $u'_{si}=-b_i,\ u'_{jt}=b_j,\ u'_{ij} =u_{ij} \ \ \forall(i,j) \in A$

sia $x$ il flusso di valore massimo sul grafo $(N',A')$

se il valore di $x$ è uguale a $\sum\limits_{i\in N, b_i>0}b_i$ (cioè tutti gli archi di $A'\backslash A$ sono saturi)

allora $x$ è ammissibile per il problema del flusso di costo minimo,

altrimenti il flusso di costo minimo non ammette soluzioni ammissibili

## Algoritmi risolutivi

1. [[Algoritmo dei cammini minimi successivi ]]
