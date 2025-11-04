---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic:
---
# Ricerca in profondita BackTracking (BDF)
---
la **Ricerca in profondità** o **BackTracking depth-first** (**BDF**) è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] variante della[[Ricerca in profondita (DF)| ricerca in profondita]] che oltre a **non** salvare i nodi raggiunti  **NON** salva la **frontiera**, ma utilizza la [[Ricorsione|ricorsione]] per risalire i nodi una volta l'algoritmo non trova piu un successore valido risale le chiamate di funzione e generare il prossimo stato da esplorare.  

```pseudo
	\begin{algorithm}
	\caption{Algo Caption}
	\begin{algorithmic}
\Function{Backtracking-Search}{$csp$}
    \Return \Call{Recursive-Backtracking}{$\{\}, csp$}
\EndFunction

\Function{Recursive-Backtracking}{$assignment, csp$}
    \If{$assignment$ is complete}
        \Return $assignment$
    \EndIf
    \State $var \gets$ \call{Select-Unassigned-Variable}{$\text{Variables}[csp], assignment, csp$}
    \For{each $value$ in \call{Order-Domain-Values}{$var, assignment, csp$}}
        \If{$value$ is consistent with $assignment$ given $\text{Constraints}[csp]$}
            \State $assignment \gets assignment \cup \{var = value\}$
            \State $result \gets$ \Call{Recursive-Backtracking}{assignment, csp}
            \If{$result \neq \text{failure}$}
                \Return $result$
            \EndIf
            \State $assignment \gets assignment \setminus \{var = value\}$
        \EndIf
    \EndFor
    \Return failure
\EndFunction
\end{algorithmic}
	\end{algorithm}
```


##  Analisi della complessità
 [[Complessita|complessità in spazio]] in spazio diventa  $O(m)$
