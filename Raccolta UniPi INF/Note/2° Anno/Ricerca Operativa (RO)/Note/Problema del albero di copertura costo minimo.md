---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Problema del albero di copertura costo minimo
---

### Definizione

Dato un [[Grafo|grafo]] $G = (N, A)$ non orientato, in cui ad ogni arco $\{i, j\} \in A$ è associato un costo $c_{ij}$, trovare un [[Albero di copertura]] $T$ di costo minimo ,dove il costo di $T$  è definito come  $\sum_{\{i,j\}\in T}c_{ij}$

Senza perdita di generalità , possiamo supporre che il grafo $G$  sia completo,
eventualmente aggiungendo archi di costo $M$, dove $M$ è una costante
sufficientemente grande $M >\begin{subarray}{}\max \\ \{i,j∈A\}\end{subarray}cij$

## Modello 1

### Variabili decisionali

Dati i nodi del grafo $N = \{1,\dots,n\}$

per ogni $i,j \in N$ con $i<j$ , definiamo le variabili decisionali:

$$
x_{ij} =
\begin{cases}
1 \ \ \
\text{se l' albero contine l' arco } (i,j) \\

0  \ \ \ \text{altrimenti}
\end{cases}
$$

### modello  di ottimizzazione:

$$
\begin{cases}
\min
\sum\limits_{i \in N}
\sum\limits_{
\substack{j\in N \\ j>i}}
c_{ij}x_{ij} \\

\sum\limits_{i \in N}
\sum\limits_{
\substack{j\in N \\ j>i}}
 x_{ij} = n-1
\ \ \ \ \ \ \ \ \ \ \ \ \ \
\text{l'albero contiene } n-1 \text{ archi}
\\

\sum\limits_{i \in S}
\sum\limits_{
\substack{j\in S \\ j>i}}
\leq |S| -1
\ \ \ \ \ \ \ \ \ \ \ \ \ \  \begin{subarray}{}
\forall S \subset N \ : \ |S| \geq 3 \\
\text{ eliminazione dei cicli}
\end{subarray}
\\

x_{ij} \in \{0,1\}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  i,j \in N  \text{ con } i<j

\end{cases}
$$

- il primo vincolo serve a prendere tutto i nodi almeno una volta
- il secondo vincolo serve ad evitare cicli evitando cosi che un nodo venga raggiunto più volte da archi diversi

## Modello 2

### Variabili decisionali

Dati i nodi del grafo $N = \{1,\dots,n\}$

per ogni $i,j \in N$ con $i<j$ , definiamo le variabili decisionali:

$$
x_{ij} =
\begin{cases}
1 \ \ \
\text{se l' albero contine l' arco } (i,j) \\

0  \ \ \ \text{altrimenti}
\end{cases}
$$

### modello  di ottimizzazione:

$$
\begin{cases}
\min
\sum\limits_{i \in N}
\sum\limits_{
\begin{subarray}{}
j\in N \\ j>i
\end{subarray}}c_{ij}x_{ij} \\

\sum\limits_{i \in N}
\sum\limits_{
\begin{subarray}{}
j\in N \\ j>i
\end{subarray}} x_{ij} = n-1
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
\text{l'albero contiene } n-1 \text{ archi}
\\

\sum\limits_{i \in S}
\sum\limits_{
\begin{subarray}{}
j \not\in S \\ j>i
\end{subarray}} x_{ij} +
\sum\limits_{i \not\in S}
\sum\limits_{
\begin{subarray}{}
j \in S \\ j>i
\end{subarray}} x_{ij}
\geq  1
\ \ \ \
\begin{subarray}{}
\forall S \subset N \ : \ |S| \geq 1 \\
\text{ vincolo di connesione}
\end{subarray}
\\

x_{ij} \in \{0,1\}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  i,j\in N \text{ con } i<j

\end{cases}
$$

- il primo vincolo serve a prendere tutto i nodi almeno una volta
- il secondo vincolo controlla che tutto i nodi siano connessi , questo unito al primo vincolo evita che un nodo venga raggiunto due volte con archi diversi