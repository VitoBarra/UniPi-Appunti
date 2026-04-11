---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---

# Problema del flusso massimo
---
Nel **Problema del flusso massimo** si considera un [[Graph Theory|grafo]] orientato $G=(N,A)$ con una capacita superiore $u_{ij}$ associata a ogni arco $(i,j) \in A$.
Fissati un nodo sorgente $s \in N$ e un nodo pozzo $t \in N$, l'obiettivo e inviare la massima quantità possibile di [[Flusso su grafo|flusso]] da $s$ a $t$ senza violare le capacita degli archi.

L'idea e distribuire il flusso nella rete in modo che:
- nessun arco trasporti piu della sua capacita
- il flusso si conservi in tutti i nodi diversi da $s$ e $t$
- la quantita totale spedita da $s$ a $t$ sia massima
![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/IMG - problema del flusso massimo - 01.png]]

## Formulazione come PL
Variabili decisionali:
- $x_{ij}$ = [[Flusso su grafo|flusso]] sull'arco $(i,j)$, per ogni $(i,j) \in A$
- $v$ = valore totale del flusso, cioe flusso totale uscente da $s$ ed equivalentemente flusso totale entrante in $t$
La [[Programmazione lineare|formulazione di programmazione lineare]] del problema e:

$$
\begin{cases}
\max v \\
\sum\limits_{(i,s) \in A} x_{is}-\sum\limits_{(s,j) \in A} x_{sj} =-v \\
\sum\limits_{(i,t) \in A} x_{it}-\sum\limits_{(t,j) \in A} x_{tj} =v \\
\sum\limits_{(i,k) \in A} x_{ik}-\sum\limits_{(k,j) \in A} x_{kj} =0 \qquad \forall k \in N \backslash \{s,t\}\\
0 \leq x_{ij} \leq u_{ij} \qquad \forall(i,j) \in A
\end{cases}
$$

La funzione obiettivo massimizza il valore del flusso. I vincoli impongono il bilancio nei nodi e il rispetto delle capacita sugli archi.

# Taglio ammissibile 
Un **taglio ammissibile** è un [[Taglio su grafo|taglio su grafo]] $(N_s,N_t)$ tale che $s \in N_s$ e $t \in N_t$.
Dato un taglio ammissibile $(N_s,N_t)$ ed un flusso $x$, si definiscono:
- $A^+ = \{(i,j)\in A\ |\ i\in N_s, j\in N_t\}$ insieme degli archi diretti del taglio
- $A^- = \{(i,j)\in A\ |\ i\in N_t, \ j\in N_s\}$ insieme degli archi inversi del taglio
- $u(N_s,N_t) = \sum\limits_{(i,j)\in A^+} u_{ij}$ capacita del taglio
- $x(N_s,N_t) = \sum\limits_{(i,j)\in A^+} x_{ij} -\sum\limits_{(i,j)\in A^-} x_{ij}$ flusso sul taglio

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/IMG - problema del flusso massimo - 02.png]]

### Lemma

Se $x$ è un [[Flusso su grafo|flusso]] ammissibile e $(N_s,N_t)$ è un [[Taglio su grafo|taglio]] ammissibile, allora

1. $v=x(N_s,N_t)$ (valore del flusso = flusso sul taglio)
2. $x(N_s,N_t) \leq u(N_s,N_t)$ (flusso sul taglio $\leq$ capacita del taglio)
 
**Dimostrazione**
a) Consideriamo i vincoli di bilancio corrispondenti ai nodi di $N_t$:

$$
\sum\limits_{(i,k)\in A} x_{ik} - \sum\limits_{(k,j)\in A} x_{kj} = 0 \qquad \forall k \in N_t \setminus \{t\}
$$

$$
\sum\limits_{(i,t)\in A} x_{it} - \sum\limits_{(t,j)\in A} x_{tj} = v
$$

Sommando tra loro le equazioni, si ottiene $v = x(N_s,N_t)$.

b) Utilizzando i vincoli di capacità $0 \leq x \leq u$, si ottiene

$$
x(N_s,N_t) = \sum\limits_{(i,j)\in A^+} x_{ij} - \sum\limits_{(i,j)\in A^-} x_{ij} \leq \sum\limits_{(i,j)\in A^+} u_{ij} = u(N_s,N_t).
$$



# Interpretazione dei cammini aumentanti

Nel problema del flusso massimo, l'esistenza di un [[Cammino aumentante|cammino aumentante]] nel [[Grafo residuo|grafo residuo]] equivale alla possibilità di aumentare il valore del flusso corrente.

Il punto importante è che il [[Grafo residuo|grafo residuo]] non contiene solo archi "in avanti" ancora disponibili, ma anche archi all'indietro che rappresentano la possibilità di annullare parte del flusso già inviato. Per questo motivo, un [[Cammino aumentante|cammino aumentante]] può anche non coincidere con un cammino orientato del grafo iniziale.

Per trovare cammini nel [[Grafo residuo|grafo residuo]] si possono usare algoritmi per cammini su grafi, ad esempio l' [[Algoritmo di Dijkstra|Algoritmo di Dijkstra]]
