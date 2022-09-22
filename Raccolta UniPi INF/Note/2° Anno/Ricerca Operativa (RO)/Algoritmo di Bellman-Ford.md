---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo di Bellman-Ford
---

### *Teorema*

L algoritmo di Bellman-Ford trova un albero dei cammini minimi oppure un ciclo orientato di costo negativo dopo al più $|N|$ iterazioni anche in caso di archi negativi

### dimostrazione

- per ogni nodo $j$ l etichetta $\pi^k_j$ è uguale al costo del cammino minimo da $r$  a $j$ che contiene al più $k$ archi
- Se ad una interazione $k \leq |N|$ le etichette dei nodi non sono state modificate $(\pi^k=\pi^{k-1})$ allora rimarranno costanti in tutte le iterazioni successive, quindi $\pi^k_j$ è il costo del cammino minimo da $r$ a $j$ senza limitazioni sul numero di archi e $p$ fornisce un albero ottimo.
- se al nitrazione $|N|$ viene modificata l etichetta di un nodo $j$, allora è stato trovato un nuovo cammino da $r$ a $j$ contenente $|N|$ archi (cioè passante due volte su uno stesso nodo) di costo inferiore rispetto a tutti i cammini semplici da $r$ a $j$. pertanto non può esistere un cammino minimo da $r$ a $j$  mentre nel nuovo cammino trovato esiste un ciclo di costo negativo che può essere ricavato dal vettore $p$

### *Algoritmo*

1. Inizializza l albero con nodi fittizi da $r$ a tutto gli altri nodi

    $$
    p_i =
    \begin{cases}
    0  \ \ \ \ \ \ \ \ se \ \ i=r \\
    -1  \ \ \ \ \ se \ \ i\not=r \\
    \end{cases}
    \ \ \ \ \ \ \ \ \ \ \
    \pi^0_i=
    \begin{cases}
    0  \ \ \ \ \ \ \ \ \ \ se\ \  i=r \\
    +\infty  \ \ \ \ \ se\ \ i\not=r \\
    \end{cases}
    \ \ \ \ \ \ \ \ \
    k=1
    $$

2. [aggiorniamo le etichette di tutti i nodi]
per ogni nodo $j \in N$:
        trova $u=\arg \min_{i\in BS(j)} \{ \pi^{k-1}_i+c_{ij}\}$
        ($BS(j) = \{i \in N: \text{esiste un arco }(i,j)\in A\}$ è la stella entrante in $j$)
 se $\pi^{k-1}_j > \pi^{k-1}_u+c_{uj}$
    1. **allora** $p_j = u,\ \  \pi^{k}_j =\pi^{k-1}_u+c_{uj}$-
    2. **altrimenti** $\pi^{k}_j =\pi^{k-1}_j$
3. Se $\pi^k=\pi^{k-1}$ allora **STOP** e $p$  fornisce un albero ottimo
4. Se $k=|N|$
    1. **allora** **STOP** e $p$ fornisce un ciclo orientato di costo negativo
    2. **altrimenti** $k=k+1$ e torna al passo 2

### Osservazioni:

ad ogni iterazione $k$ l algoritmo mantiene

- un albero di copertura radicato in r e orientato memorizzato in un vettore $p$ di predecessori
- un vettore $\pi^k$ di etichette associate ai nodi che non è necessariamente uguale al vettore dei potenziali dei nodi associato al albero

### Commetto da sistemare

in generale l etichetta in più rende il vettore $\pi$ una matrice $n \times n$ in pratica $n$ nodi per $n$  etichette

>[!example]-  Esempio
![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/-RO Media/Untitled 3 1.png]]
