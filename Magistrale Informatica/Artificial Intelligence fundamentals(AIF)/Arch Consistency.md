---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Arch Consistency
---

```pseudo
\begin{algorithm}
\caption{Arch Consistency}
\begin{algorithmic}	
\Function{AC-3}{$csp$} \Returns the CSP, possibly with reduced domains
\Input{$csp$, a binary CSP with variables $\{X_1, X_2, \ldots, X_n\}$}
\State $queue \gets$ a queue of arcs, initially all the arcs in $csp$
\While{$queue$ is not empty}
    \State $(X_i, X_j) \gets \text{Remove-First}(queue)$
    \If{\Call{Remove-Inconsistent-Values}{$X_i, X_j$}}
        \For{each $X_k$ in $\text{Neighbors}[X_i]$}
            \State add $(X_k, X_i)$ to $queue$
        \EndFor
    \EndIf
\EndWhile
\Return $csp$
\EndFunction

\Function{Remove-Inconsistent-Values}{$X_i, X_j$} \Returns true iff succeeds
\State $removed \gets \text{false}$
\For{each $x$ in $\text{Domain}[X_i]$}
    \If{no value $y$ in $\text{Domain}[X_j]$ allows $(x,y)$ to satisfy the constraint $X_i \leftrightarrow X_j$}
        \State delete $x$ from $\text{Domain}[X_i]$
        \State $removed \gets \text{true}$
    \EndIf
\EndFor
\Return $removed$
\EndFunction
\end{algorithmic}
\end{algorithm}
```