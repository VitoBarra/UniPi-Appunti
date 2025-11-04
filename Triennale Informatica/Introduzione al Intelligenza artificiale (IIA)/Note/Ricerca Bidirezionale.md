---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca Bidirezionale
---
la **Ricerca Bidirezionale** è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] applicabile in cui la ricerca
- in **avanti o guidata dai dati**: si esplora lo spazio di ricerca dallo stato iniziale allo stato obiettivo; 
- all’**indietro o guidata dall’obiettivo**: si esplora lo spazio di ricerca a partire da uno stato goal e riconducendosi a sotto-goal fino a trovare uno stato iniziale.
si basa sul idea che se si è trovata una soluzione allora c è un intersezione tra le due esplorazioni 
![[Pasted image 20230212023837.png]]
Questo algoritmo puo essere applicato solo **_sotto condizioni_** questo sono:
- Si può definire facilmente uno **stato finale** o più stati finali eventualmente connessi ad uno stato finale "**dummy**". Potrebbero esserci dei problemi per cui questo non è possibile
- si può generare lo stato predecessore di uno stato, questo è facile quando tutte le azioni sono reversibili


un implementazione pseudo codice è la seguente:
```pseudo
	\begin{algorithm}
	\caption{BI-DIRECTIONAL-SEARCH}
	\begin{algorithmic}
\Function{BiBF-Search}{$problem_F, f_F, problem_B, f_B$}
    \State $node_F \gets Node(problem_F.\text{INITIAL})$
    \State $node_B \gets Node(problem_B.\text{INITIAL})$
    \State $frontier_F \gets$ a priority queue ordered by $f_F$, with $node_F$ as an element
    \State $frontier_B \gets$ a priority queue ordered by $f_B$, with $node_B$ as an element
    \State $reached_F \gets$ a lookup table, with one key $node_F.\text{STATE}$ and value $node_F$
    \State $reached_B \gets$ a lookup table, with one key $node_B.\text{STATE}$ and value $node_B$
    \State $solution \gets$ failure
    \While{not \Call{Terminated}{$solution, frontier_F, frontier_B$}}
        \If{$f_F(\text{TOP}(frontier_F)) < f_B(\text{TOP}(frontier_B))$}
            \State $solution \gets$ \Call{Proceed}{$F, problem_F, frontier_F, reached_F, reached_B, solution$}
        \Else
            \State $solution \gets$ \Call{Proceed}{$B, problem_B, frontier_B, reached_B, reached_F, solution$}
        \EndIf
    \EndWhile
    \Return $solution$
\EndFunction

\Function{Proceed}{$dir, problem, frontier, reached, reached_2, solution$}
    \State $node \gets$ \Call{Pop}{$frontier$}
    \ForAll{$child$ in \Call{Expand}{$problem, node$}}
        \State $s \gets child.\text{STATE}$
        \If{$s \notin reached$ \textbf{or} \Call{Path-Cost}{$child$} $<$ \Call{Path-Cost}{$reached[s]$}}
            \State $reached[s] \gets child$
            \State add $child$ to $frontier$
            \If{$s \in reached_2$}
                \State $solution_2 \gets$ \Call{Join-Nodes}{$dir, child, reached_2[s]$}
                \If{\Call{Path-Cost}{$solution_2$} $<$ \Call{Path-Cost}{$solution$}}
                    \State $solution \gets solution_2$
                \EndIf
            \EndIf
        \EndIf
    \EndFor
    \Return $solution$
\EndFunction
\end{algorithmic}
	\end{algorithm}
```


### Analisi
[[Complessita]]
- _Strategia  completa_ se si esplora con [[Ricerca in ampiezza (BF)|BF]]
- _Strategia  ottimale_
-  _Complessità nel tempo_  $O(b^{d/2})$
	- il consto totale $b^{d/2} +b^{d/2}$ 
- _Complessità spazio_ (nodi in memoria): $O(b^{d/2})$ _Cammino dalla radice goal_ + _cammino da goal a radice_ 