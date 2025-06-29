---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Algoritmo per risolvere CSP con struttura ad albero
---




```pseudo
\begin{algorithm}
\caption{Tree-CSP-Solver for CSP}
\begin{algorithmic}

\FUNCTION{TREE-CSP-SOLVER}{csp} \COMMENT{Returns a solution or failure}
    \STATE \textbf{inputs:} $csp$, a CSP with components $X$, $D$, $C$
    \STATE $n \gets$ number of variables in $X$
    \STATE $assignment \gets$ an empty assignment
    \STATE $root \gets$ any variable in $X$
    \STATE $X \gets$ \CALL{TOPOLOGICALSORT}{$X$, $root$}
    
    \FOR{$j = n$ down to $2$}
        \STATE \CALL{MAKE-ARC-CONSISTENT}{PARENT($X_j$), $X_j$}
        \IF{it cannot be made consistent}
            \RETURN failure
        \ENDIF
    \ENDFOR

    \FOR{$i = 1$ to $n$}
        \STATE $assignment[X_i] \gets$ any consistent value from $D_i$
        \IF{there is no consistent value}
            \RETURN failure
        \ENDIF
    \ENDFOR

    \RETURN $assignment$
\ENDFUNCTION

```