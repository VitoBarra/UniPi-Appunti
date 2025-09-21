---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca con approfondimento iterativo IDS
---
la **Ricerca ad approfondimento iterativo** o **iterative deepening search** (**IDS**) è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] che utilizza i concetti di [[Ricerca in ampiezza (BF)|Ricerca in ampiezza]] e di [[Ricerca in profondita limitata (DLS)|Ricerca in profondità limitata]], rappresentando un buon compromesso tra i due approcci. Ottiene infatti le buone proprietà di completezza e ottimalità della prima e il basso consumo di memoria della seconda.

L'algoritmo esplora più volte l’albero incrementando progressivamente il limite $\ell$ a partire da $0$, poi $1$, poi $2$, e così via. Ogni iterazione esegue una [[Ricerca in profondita limitata (DLS)|Ricerca in profondità limitata]] con il nuovo limite, procedendo in profondità fino al taglio del branch completamente esplorato. 

![[IMG - Ricerca in profondita iterativa DL.png]]
questa ricerca puo essere implementata come:
```pseudo
\begin{algorithm}
\caption{Iterative Deepening Search}
\begin{algorithmic}
\Function{Iterative-Deepening-Search}{problem}
    \For{depth $= 0$ to $\infty$}
        \State result $\gets$ \Call{Depth-Limited-Search}{problem, depth}
        \If{result $\neq$ cutoff}
            \Return result
        \EndIf
    \EndFor
\EndFunction
\end{algorithmic}
\end{algorithm}
```

Durante l'esecuzione, i nodi vicini alla radice vengono generati più volte, ma la maggior parte dei nodi si trova nei livelli inferiori, che vengono generati una sola volta. 
### Analisi della complessità
Siano:
- $b$ = fattore di ramificazione (*Branching factor*), cioè il numero massimo di successori
- $d$ = profondità del nodo obiettivo più superficiale (*Depth*)
- $m$ = lunghezza massima dei cammini nello spazio degli stati (*Max*)

- **Completa**: in **spazzi finiti** e **aciclici** o con finiti con cicli ma usando [[Algoritmi di riconoscimento cicli|cycle detection]] prima o poi esplora tutti i nodi fino alla soluzione come per la [[Ricerca in ampiezza (BF)|Ricerca in ampiezza]]
- **Ottimale**: Se tutti i costi sono uguali come per la [[Ricerca in ampiezza (BF)|Ricerca in ampiezza]]
- **_[[Complessita]] nel tempo_**: $O(b^d)$ se la soluzione esiste o $O(b^m)$ se non esiste, questo viene dal fatto che nonostante i nodi gia visti sono generati più volte il comportamento asintotico resta uguale a quella della [[Ricerca in ampiezza (BF)|BF]] infatti: $N(IDS) = db+(d-1)b^2+(d-2)b^3+\dots+1b^d=O(b^d)$ 
- **_[[Complessita]] in spazio_**: $O(bd)$ quando esiste una soluzione o $O(bm)$ quando una soluzione non c è 
