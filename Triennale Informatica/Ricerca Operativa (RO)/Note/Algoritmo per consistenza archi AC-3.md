---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - AIGenerated
Area: 
topic: 
SubTopic:
---

# Algoritmo per consistenza archi AC-3
---
l [[Algoritmi|algoritmo]] **AC-3** è usato nel contesto del [[Problemi di soddisfacibilita vincolata (CSP)|constraint satifaction problem (CSP)]] per ridurre i domini delle variabili in modo che siano **arc consysten**.

Per fare ciò **AC-3** gestisce una coda di archi da verificare, inizialmente popolata con tutti gli archi bidirezionali del CSP. L’algoritmo procede estraendo un arco $(X_i, X_j)$ e verificando la consistenza di $X_i$ rispetto a $X_j$. Se il dominio $D_i$ viene ridotto, si reinseriscono nella coda tutti gli archi incidenti su $X_i$ per favorire ulteriori propagazioni. Se un dominio si svuota, il CSP risulta insoddisfacibile. In assenza di ulteriori riduzioni, si ottiene un CSP equivalente, ma più efficiente, caratterizzato da domini ridotti. La complessità computazionale dell’algoritmo AC-3 è stimabile come: $O(c \cdot d^3)$ dove $c$ rappresenta il numero di vincoli binari e $d$ la dimensione massima dei domini.

lo pseudo codice del algoritmo AC-3: 
```pseudo
\begin{algorithm}
\caption{AC-3}
\begin{algorithmic}
\Function{AC-3}{csp}
    \State $queue \gets$ coda di archi, inizialmente tutti gli archi in \textit{csp}
    \While{queue non è vuota}
        \State $(X_i, X_j) \gets \text{Pop(queue)}$
        \If{\Call{REVISE}{csp, $X_i$, $X_j$}}
            \If{dimensione di $D_i = 0$}
                \Return \textbf{false}
            \EndIf
            \ForAll{$X_k \in \text{NEIGHBORS}(X_i) - \{ X_j \}$}
                \State aggiungi $(X_k, X_i)$ a $queue$
            \EndFor
        \EndIf
    \EndWhile
    \Return \textbf{true}
\EndFunction

\State

\Function{REVISE}{csp, $X_i$, $X_j$}
    \State $revised \gets \textbf{false}$
    \ForAll{$x \in D_i$}
        \If{nessun valore $y \in D_j$ soddisfa il vincolo tra $X_i$ e $X_j$ con $(x, y)$}
            \State rimuovi $x$ da $D_i$
            \State $revised \gets \textbf{true}$
        \EndIf
    \EndFor
    \Return $revised$
\EndFunction
\end{algorithmic}
\end{algorithm}
```