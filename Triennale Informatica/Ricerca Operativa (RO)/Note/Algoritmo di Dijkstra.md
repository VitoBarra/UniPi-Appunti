---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---


# Algoritmo di Dijkstra
---
l'**Algoritmo di Dijkstra** è un [[Algoritmi|algoritmo]] che trova un [[alberi|albero di cammini minimo]] su di un [[Grafi|Grafi]] 

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


L’algoritmo di Dijkstra trova un albero ottimo nel caso in cui $c_{ij} \geq 0$ per ogni $(i,j) \in A$.

Ad ogni iterazione l’algoritmo mantiene:
- un albero di copertura radicato in $r$ e orientato (memorizzato in un vettore $p$ di predecessori)
- un vettore $\pi$ di potenziali dei nodi corrispondente all’albero memorizzato in $p$
- un insieme $U$ di nodi tale che gli archi che potrebbero violare le condizioni di Bellman devono essere uscenti da nodi di $U$.




Se nel [[grafi|grafo]] esistono archi di **costo negativo**, I'**algoritmo di Dijkstra** non è garantito che trovi un [[Alberi|albero]] dei cammini minimi.


### *Teorema*

Se $c_{ij} \geq 0$ per ogni $(i,j)\in A$, allora l [[Algoritmi|Algoritmo]] di Dijkstra trova un albero dei cammini minimi dopo $|N|$ iterazioni

### dimostrazione

- durante l’esecuzione del algoritmo $\pi$ è il vettore dei potenziali dei nodi associato al albero memorizzato del votatore $p$
- il potenziale di ogni nodo non può mai aumentare durante l esecuzione del algoritmo
- quando un nodo $u$ viene estratto da $U$, il suo potenziale diventa definitivo e gli archi uscenti da $u$ soddisfano le [[Condizione di Bellman]] fino alla fine del algoritmo