---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Algoritmo 
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo di Dijkstra
---

# Algoritmo di Dijkstra

### *Teorema*

Se $c_{ij} \geq 0$ per ogni $(i,j)\in A$, allora l algoritmo di Dijkstra trova un albero dei cammini minimi dopo $|N|$ iterazioni

### dimostrazione

- durante l’esecuzione del algoritmo $\pi$ è il vettore dei potenziali dei nodi associato al albero memorizzato del votatore $p$
- il potenziale di ogni nodo non può mai aumentare durante l esecuzione del algoritmo
- quando un nodo $u$ viene estratto da $U$, il suo potenziale diventa definitivo e gli archi uscenti da $u$ soddisfano le condizioni di Bellman fino alla fine del algoritmo

### *Algoritmo*

1. Inizializza

    $$
    p_i =
    \begin{cases}
    0  \ \ \ \ \ \ \ \ se \ \ i=r \\
    -1  \ \ \ \ \ se \ \ i\not=r \\
    \end{cases}
    \ \ \ \ \ \ \ \ \ \ \
    \pi_i=
    \begin{cases}
    0  \ \ \ \ \ \ \ \ \ \ se\ \  i=r \\
    +\infty  \ \ \ \ \ se\ \ i\not=r \\
    \end{cases}
    \ \ \ \ \ \ \ \ \
    U=N
    $$

2. se $U = \emptyset$ allora stop
3. Seleziona un nodo $u \in U$ con potenziale minimo $u=\arg\min_{i\in U}\pi_i$ 
4. \[Controlla le condizioni di Bellman sugli archi uscenti da $u$\]
per ogni arco $(u,v)\in A$ se $\pi_v > \pi_u +c_{uv}$ allora
    1. $p_v=u$
    2.  $\pi_v=\pi_u+c_{uv}$
5. $U=U\backslash \{u\}$ e torna al passo 1.

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 4.png]]

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 2.png]]

### Svantaggi

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2 2.png]]


> [!note]
> di solito per selezionare il nodo minimo si salvano i nodi in una [[Code di Priorità|coda di priorità]] dove si utilizzano i potenziali come chiave di ordinamento 