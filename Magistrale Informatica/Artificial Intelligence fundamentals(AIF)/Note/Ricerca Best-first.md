---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic:
---

# Ricerca Best-first
---
l algoritmo **Best-first** è un [[Algoritmi di ricerca non informati|algoritmo di ricerca]] generico dove si sceglie di espandere il nodo della **frontiera** che ha il costo minore, il costo è assegnato da una data **funzione di valutazione** $f$

lo pseudo codice:
```pseudo
\begin{algorithm}
\caption{Best-first}
\begin{algorithmic}
	\Function{Best-First-Search}{problem, $f$} 
	    \State $node \gets \text{Node}(\text{State}=\text{problem.Initial})$
	    \State $frontier \gets$ a priority queue ordered by $f$, with $node$ as an element
	    \State $reached \gets$ a lookup table, with one entry with key $\text{problem.Initial}$ and value $node$
	    \While{not \call{Is-Empty}{frontier}}
	        \State $node \gets \text{Pop}($frontier$)$
	        \If{$\text{problem.Is-Goal}($node.State$)$} 
	            \Return $node$
	        \EndIf
	        \For{each $child$ in \call{Expand}{problem, node}}
	            \State $s \gets child.\text{State}$
	            \If{$s$ is not in $reached$ or $child.\text{Path-Cost} < reached[s].\text{Path-Cost}$}
	                \State $reached[s] \gets child$
	                \State add \textit{child} to \textit{frontier}
	            \EndIf
	        \EndFor
	    \EndWhile
	    \Return failure
	\EndFunction


	\end{algorithmic}
	\end{algorithm}
```