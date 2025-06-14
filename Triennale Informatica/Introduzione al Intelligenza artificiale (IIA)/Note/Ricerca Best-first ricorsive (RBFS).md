---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca Best-first ricorsive (RBFS)
---
è un [[Algoritmi di ricerca informata|Algoritmo di ricerca informata]] basato su [[Ricerca A-Star|A*]] simile a [[Ricerca in profondita BackTracking (BDF)|DF Ricorsivo]] 

- Tiene traccia dal ogni livello del migliore percorso alternativo.
- interrompe l esplorazione quando trova un nodo meno promettente (considerando $f$)
- nel tornare indietro ricorda il miglior nodo che ha trovato nel sottalbero esplorato, per poterci eventualmente tornare

$d=$ profondità della soluzione 
_Complessita in spazio_ : $O(d)$
```pseudo
\begin{algorithm}
\caption{Ricerca Best First Ricorsiva}
\begin{algorithmic}
\Function{Ricerca-Best-First-Ricorsiva}{problema}
    \State \textbf{returns} soluzione oppure fallimento
    \State \Return \Call{RBFS}{problema, \Call{CreaNodo}{problema.Stato-iniziale}, $\infty$} \Comment{all'inizio f-limite è un valore molto grande}
\EndFunction

\Function{RBFS}{problema, nodo, f-limite}
    \State \textbf{returns} soluzione oppure fallimento e un nuovo limite all' f-costo \Comment{restituisce due valori}
    \If{\Call{problema.TestObiettivo}{nodo.Stato}}
        \Return \Call{Soluzione}{nodo}
    \EndIf
    \State $successori \gets [\ ]$
    \For{each $azione$ in \Call{problema.Azioni}{nodo.Stato}}
        \State aggiungi \Call{Nodo-Figlio}{problema, nodo, azione} a $successori$ \Comment{genera i successori}
    \EndFor
    \If{$successori$ è vuoto}
        \Return fallimento, $\infty$
    \EndIf
    \For{each $s$ in $successori$} \Comment{valuta i successori}
        \State $s.f = \max(s.g + s.h, nodo.f)$ \Comment{un modo per rendere monotona f}
    \EndFor
    \State
    \While{true}
        \State $migliore =$ il nodo con $f$ minimo tra i $successori$
        \If{$migliore.f > f\_limite$}
            \Return fallimento, $migliore.f$
        \EndIf
        \State $alternative =$ il secondo nodo con $f$ minimo tra i $successori$
        \State $risultato, migliore.f =$ \Call{RBFS}{problema, $migliore$, $\min(f\_limite, alternative)$}
        \If{$risultato \neq$ fallimento}
            \Return $risultato$
        \EndIf
    \EndWhile
\EndFunction
\end{algorithmic}
\end{algorithm}
```