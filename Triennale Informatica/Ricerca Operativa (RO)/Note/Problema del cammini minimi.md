---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---


# Problema del cammini minimi
---

### Definizione
sia $G(N,A)$ un [[Struttura dati - Grafo|grafo]] orientato in cui  definito un costo $c_{ij}$ per ogni arco $(i,j)\in A$ Dati un nodo origine $s \in N$ e un nodo destinazione $t\in N$, trovare un [[cammini su grafi|cammino orientato]] da $s$ a $t$ di costo minimo, dove il costo di un cammino è definito come la soma dei costi degli archi da cui è formato

## Modello

per goni $(i,j) \in a$, definiamo $x_{ij} =$ numero di volte che si attraversa l arco $(i,j)$ $[$flusso sul arco $(i,j)]$

$$
\begin{cases}
\min\sum\limits_{(i,j)\in A}c_{ij}x_{ij} \\
\sum\limits_{(i,s)\in A}x_{is}- \sum\limits_{(s,j)\in A}x_{sj} = -1 \\
\sum\limits_{(i,t)\in A}x_{it}- \sum\limits_{(t,j)\in A}x_{tj} = 1 \\
\sum\limits_{(i,k)\in A}x_{ik}- \sum\limits_{(k,j)\in A}x_{kj} = 0\ \ \ \ \ \ \ \ \forall k \in N \backslash \{s,t\}
\end{cases}
$$

didascalia vincoli

- 1 unita di flusso deve uscire da $s$
- 1 unita di flusso deve entrare in $t$
- i nodi diversi da $s$ e $t$ sono nodi di transito

### Esempio

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 8.png]]

il [[Modelli|modello]] può essere scritto in modo più compatto utilizzando la matrice di incidenza del grafo.

la matrice di incidenza $E$ di un grafo orientato $(N,A)$ ha dimensione $|N| \times |A|$, cioè ha una riga per ogni nodo $k \in N$ ed una colonna per ogni arco $(i,j) \in A$, ed è cosi definita:

$$
E_{k,(i,j)} =
\begin{cases}
-1 \ \ \ se \ \ k =i \\
1 \ \ \ \ \ \ se \ \ k=j \\
0 \ \ altrimenti
\end{cases}
$$

il modello può essere scritto nella forma compatta

$$
\begin{cases}
\min c^Tx \\
Ex =b \\
x \geq 0 \\
x \in \mathbb{Z}^{|A|}
\end{cases}
$$

dove $c$ è il [[Vettori|vettore]] dei costi, $x$ è il vettore dei flussi e $b$ il vettore dei bilanci ai nodi

$$
b_k=
\begin{cases}
-1 \ \ \ \ se\  k=s \\
1 \ \ \ \ \ \ \ se\  k=t \\
0 \ \ \ \ \ \ \ altrimenti
\end{cases}
$$

Consideriamo ora il problema più generale di trovare un cammino di costo minimo da un nodo $r\in N$ a tutto gli altri nodi. possiamo farlo perché si può suppore che esiste un cammino da $r$ ad ogni altro nodo $i \not= r$ eventualmente aggiungendo al grafo un arco fittizio $(r,i)$ di costo $M > (n-1) \max\limits_{(i,j)\in A} c_{ij}$

### Modello

$$
\begin{cases}
\min c^Tx \\
Ex =b \\
x \geq 0 \\
x \in \mathbb{Z}^{|A|}
\end{cases}
$$

identico al altro caso ma

$$
b =
\begin{cases}
-(n-1) \ \ \ \ se \ i=r \\
1 \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ se \  i \not=r
\end{cases}
$$

## Esistenza di soluzioni ottime

il problema dei cammini minimi ammette almeno un soluzione  ottima se e solo se non esistono cicli orientati di costo negativi.

Se non esistono cicli orientato di costo negativo, allora esiste un insieme di commini minimi da $r$ ad ogni altro nodo che forma un albero di copertura radicato in $r$ e orientato


## Algoritmi Risolutivi

1. [[Algoritmo di Dijkstra]]
