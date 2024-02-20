---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Problema 
---

Prev: [[Ricerca Operativa (RO)]]

# Problema del flusso massimo
---

### Definizione

Sia $(N,A)$ un [[Struttura dati - Grafo|grafo]] orientato in cui è definita una capacita superiore $u_{ij}$ per ogni arco $(i,j) \in A$. Dati un nodo origine $s\in N$ ed un nodo destinazione $t \in N$, vogliamo spedicare la massima quantità possibile si flusso da $s$  a $t$ in modo da rispettare le capacita superiori degli archi.

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 17.png]]

### Variabili:

- $x_{ij} =$  flusso sull’arco $(i,j)$, per ogni $(i,j) \in A$
- $v =$ flusso totale uscente del nodo $s$ (o flusso totale entrante nel nodo $t$)

## Modello di PL:

$$
\begin{cases}
\max v \\
\sum\limits_{(i,s) \in A} x_{is}-\sum\limits_{(s,j) \in A} x_{sj} =-v \\
\sum\limits_{(i,t) \in A} x_{it}-\sum\limits_{(t,j) \in A} x_{tj} =v \\
\sum\limits_{(i,k) \in A} x_{ik}-\sum\limits_{(k,j) \in A} x_{kj} =0 \ \ \ \ \ \ \ \ \ \forall k \in N \backslash \{s,t\}\\
0 \leq x_{ij} \leq u_{ij} \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \forall(i,j) \in A
\end{cases}
$$

# Flussi e tagli

un taglio è una [[Partizione di un insieme|partizione]] di $N$ in due sottoinsiemi $(N_s,N_t)$

Un taglio ammissibile è un taglio $(N_s,N_t)$ tale che $s \in N_s$ e $t \in N_t$

Dato un taglio ammissibile $(N_s,N_t)$ ed un flusso $x$, si definisco:

$A^+ = \{(i,j)\in A\ |\ i\in N_s, j\in N_t\}$ insieme degli archi diretti del taglio

$A^- = \{(i,j)\in A\ |\ i\in N_t, \ j\in N_s\}$ insieme degli archi inversi del taglio

$u(N_s,N_t) = \sum\limits_{(i,j)\in A^+} u_{ij}$                            capacita del taglio

$x(N_s,N_t) = \sum\limits_{(i,j)\in A^+} x_{ij} -\sum\limits_{(i,j)\in A^-} x_{ij}$    flusso sul taglio

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 10.png]]

### Lemma

Se $x$ è un flusso ammissibile e $(N_s,N_t)$ è un taglio ammissibile, allora

1. $v=x(N_s,N_t)$ (valore del flusso = flusso sul taglio)
2. $x(N_s,N_t) \leq u(N_s,N_t)$ (flusso sul taglio $\leq$ capacita del taglio)

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2 7.png]]



---

# Grafo residuo

Il teorema $\max$ flow - $min$ cut fornisce una condizione sufficiente di ottimalità.

Ma come si trova (se esiste) un taglio ammisibile $(N_s,N_t)$ tale che $x(N_s,N_t)=u(N_s,N_t)$?

Dato un flusso ammissibile $x$, il grafo residuo relativo ad $x$ è il grafo $G(x)=(N,A(x))$ avente gli stessi nodi del grafo $G$, mentre gli archi e le loro capacità residue $r_{ij}$ sonjo definiti come segue:

se $(i,j) \in A$ con $x_{ij} < u_{ij}$ (arco non saturo) allore $(i,j) \in A(x)$ con $r_{ij} = u_{ij}-x_{ij}$

se $(i,j) \in A$ con $x_{ij} > 0$ (arco non vuoto) allora $(j,i) \in A(x)$ con $r_{ji} =x_{ij}$

---

## Cammino aumentante

Dato un flusso ammissibile $x$, un cammino aumentante rispetto ad $x$ è un cammino orientato da $s$ a $t$ nel grafo residuo $G(x)$



![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 3 5.png]]

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 4 3.png]]

1-2-5-6 e un cammino aumentante (e un cammino orientato nel grafo iniziale)

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 5 2.png]]

1-2-4-5-6 e un cammino aumentate (ma non e un cammino orientato nel grafo
iniziale)

[[Condizione di Bellman]]

[[Algoritmo di Dijkstra]]

[[Problemi riducibili al Problema di flusso massimo]]
