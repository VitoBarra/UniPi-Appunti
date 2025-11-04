---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca in profondità limitata (DLS)
---
la **Ricerca in profondità limitata** o **deep limited search** (**DLS**) è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] variante della [[Ricerca in profondita (DF)|Ricerca in profondità]]. Questo algoritmo scende l albero fino ad una profondità predefinita $\ell$; da quel livello in poi i nodi vengono trattati come se non avessero successori.

Questo approccio consente di evitare che la [[Ricerca in profondita (DF)|ricerca in profondità]] si blocchi si incastri un percorso infinito.

Lo pseudo codice che restituisce il risultato se trova un nodo goal, fallisce se trova un ciclo e restituisce un valore di cutoff se raggiunge il limite prefissato è il seguente:
```pseudo
\begin{algorithm}
\caption{Depth Limited Search}
\begin{algorithmic}

\Function{Depth-Limited-Search}{problem, $\ell$}
    \State frontier $\gets$ a LIFO queue (stack) with \Call{Node}{problem.INITIAL} as an element
    \State result $\gets$ failure
    \While{not \Call{Is-Empty}{frontier}}
        \State node $\gets$ \Call{Pop}{frontier}
        \If{\Call{Is-Goal}{problem, node.STATE}}
            \Return node
        \EndIf
        \If{\Call{Depth}{node} $> \ell$}
            \State result $\gets$ cutoff
        \ElsIf{not \Call{Is-Cycle}{node}}
            \For{each child in \Call{Expand}{problem, node}}
                \State \Call{Add}{frontier, child}
            \EndFor
        \EndIf
    \EndWhile
    \Return result
\EndFunction
\State
\end{algorithmic}
\end{algorithm}
```
Esiste anche una sua implementazione ricorsiva:
```pseudo
\begin{algorithm}
\caption{Depth-Limited Search Recursive}
\begin{algorithmic}

\Function{Depth-Limited-Search}{problem, limit} 
\Return \Call{Recursive-DLS}{\Call{Make-Node}{Initial-State[problem]}, problem, limit}
\EndFunction

\State 

\Function{Recursive-DLS}{node, problem, limit} 
    \State \textit{cutoff-occurred?} $\gets$ \textit{false}
    \If{\Call{Goal-Test}{problem, State[node]}} 
        \Return \textit{node}
    \ElsIf{Depth[node] = limit} 
        \Return \textit{cutoff}
    \Else
        \For{each \textit{successor} in \Call{Expand}{node, problem}} 
            \State \textit{result} $\gets$ \Call{Recursive-DLS}{successor, problem, limit}
            \If{\textit{result} = \textit{cutoff}} 
                \State \textit{cutoff-occurred?} $\gets$ \textit{true}
            \ElsIf{\textit{result} $\neq$ \textit{failure}} 
                \Return \textit{result}
            \EndIf
        \EndFor
        \If{\textit{cutoff-occurred?}} 
            \Return \textit{cutoff}
        \Else 
            \Return \textit{failure}
        \EndIf
    \EndIf
\EndFunction
\end{algorithmic}
\end{algorithm}
```

La scelta del limite $\ell$ è fondamentale per il successo dell'algoritmo: un valore troppo basso rischia di non raggiungere la soluzione, mentre un valore troppo alto può riportare i problemi tipici della [[Ricerca in profondita (DF)|Ricerca in profondità]] classica.  In alcuni casi, è possibile stabilire un limite efficace grazie alla conoscenza del dominio. come ad esempio usando il [[Grafi|diametro del grafo]] su cui si pone l'albero di ricerca.

### Analisi della complessità

Siano:
- $b$ = fattore di ramificazione (*Branching factor*), ovvero il numero massimo di successori per ogni nodo
- $d$ = profondità del nodo obiettivo più superficiale (*Depth*)
- $m$ = lunghezza massima dei cammini nello spazio degli stati (*Max*)
- $\ell$ = profondità massima scelta

- _Strategia completa_ se:
	- il problema ha un limite superiore noto sulla profondità
	- se $d \leq \ell$
- _Strategia NON ottimale_
- _[[Complessita]] nel tempo_ (nodi generati): $O(b^\ell)$ 
- _[[Complessita]] in spazio_: $O(b\ell)$

>[!note]
>La [[Ricerca in profondita (DF)|DF]] può essere vista come un caso particolare di questa con $\ell = \infty$