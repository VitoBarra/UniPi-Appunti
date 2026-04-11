---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Problema del flusso di costo minimo
---
Nel [[Problema del flusso di costo minimo]] si considera un [[Graph Theory|grafo]] orientato $G=(N,A)$ in cui ogni arco $(i,j) \in A$ ha:
- una capacita superiore $u_{ij}$
- un costo unitario $c_{ij}$
Inoltre ogni nodo $k \in N$ e associato a un bilancio $b_k$:
- $b_k > 0$ se il nodo richiede flusso in ingresso
- $b_k < 0$ se il nodo fornisce flusso in uscita
- $b_k = 0$ se il nodo e di transito
L'obiettivo e trovare un [[Flusso su grafo|flusso]] ammissibile che soddisfi tutti i bilanci ai nodi e che abbia costo totale minimo.

## Formulazione come PL

Variabili decisionali:
- $x_{ij}$ = [[Flusso su grafo|flusso]] sull'arco $(i,j)$, per ogni $(i,j) \in A$
La [[Programmazione lineare|formulazione di programmazione lineare]] del problema e:

$$
\begin{cases}
\min \sum\limits_{(i,j)\in A} c_{ij}x_{ij} \\
\sum\limits_{(i,k)\in A} x_{ik}- \sum\limits_{(k,j)\in A} x_{kj} = b_k \qquad \forall k \in N\\
0 \leq x_{ij} \leq u_{ij} \qquad \forall (i,j) \in A
\end{cases}
$$

La funzione obiettivo minimizza il costo complessivo del flusso. I vincoli impongono il bilancio in ogni nodo e il rispetto delle capacita sugli archi.

### Esistenza di soluzione

Per determinare se esistono soluzioni ammissibili per il problema del flusso di costo minimo su un grafo $G(N,A)$, si può risolvere il problema del flusso massimo sul grafo $G'(N',A')$, dove:

- $N'= N \cup\{s,t\}$
- $A'=A \cup \{(s,i)\ |\ i\in N \ \ tale \ \ che \ \ b_i <0 \} \cup \{(j,t) \ | \ j \in N \ tale \ \ che\ b_i>0\}$
- $u'_{si}=-b_i,\ u'_{jt}=b_j,\ u'_{ij} =u_{ij} \ \ \forall(i,j) \in A$

Sia $x$ il flusso di valore massimo sul grafo $(N',A')$.

Se il valore di $x$ è uguale a $\sum\limits_{i\in N, b_i>0}b_i$, cioè tutti gli archi di $A'\backslash A$ sono saturi, allora $x$ è ammissibile per il problema del flusso di costo minimo.
Altrimenti il problema non ammette soluzioni ammissibili.

## Algoritmi risolutivi

1. [[Algoritmo dei cammini minimi successivi ]]
