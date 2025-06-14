---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca in ampiezza (BF)
---
la **Ricerca in ampiezza** o **Breadth-first search** (BF) è un [[Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza una [[Coda (FIFO)|coda FIFO]] per implementare la **frontiera**, si assume che il costo di ogni arco è $1$.
Il controllo del raggiungimento del nodo goal è fatto al momento della **generazione** dei nodi (**early goal test**) e non al momento del esplorazione (**late goal test**), questo riduce la [[Complessita|complessità]]


 Per la  **BF** sia su [[grafi|grafi]] che su [[Alberi|alberi]]  genera i nodi a profondità $d$ solo dopo aver generato tutti i nodi profondità $d-1$ e per questo si diche che esplora con **profondità uniforme**.  Per questa proprietà usa sempre un numero minimo di azioni per trovare il goal.
 
Applicando la **BF** su [[alberi|alberi]] visivamente si ottiene un esplorazione per livelli
![[IMG - Ricerca in ampiezza BF.png]]

l [[Algoritmi|algoritmo]] *ritorna* sempre una **nodo soluzione** o un stato di **fallimento** e segue come: 
```pseudo
\begin{algorithm}
\caption{Breadth-First Search}
\begin{algorithmic}
\Function{BREADTH-FIRST-SEARCH}{problem}
    \State $\textit{node} \gets \text{NODE}(\textit{problem.INITIAL})$
    \If{$\textit{problem.Is-Goal}(\textit{node.STATE})$}
        \Return $\textit{node}$
    \EndIf
    \State $\textit{frontier} \gets \text{a FIFO queue, with } \textit{node} \text{ as an element}$
    \State $\textit{reached} \gets \{\textit{problem.INITIAL}\}$
    \While{not $\text{Is-Empty}$($\textit{frontier}$)}
        \State $\textit{node} \gets \text{Pop}(\textit{frontier})$
        \forall{\textit{child} \textbf{in} EXPAND(\textit{problem}, \textit{node})}
            \State $s \gets \textit{child.STATE}$
            \If{$\textit{problem.Is-Goal}(s)$}
                \Return $\textit{child}$
            \EndIf
            \If{$s$ is not in $\textit{reached}$}
                \State add $s$ to $\textit{reached}$
                \State add $\textit{child}$ to $\textit{frontier}$
            \EndIf
        \EndFor
    \EndWhile
    \Return \textit{failure}
\EndFunction
\State
\end{algorithmic}
\end{algorithm}
```



### Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)

- _Strategia completa_
	-  non vengono lasciate strade non esplorate siccome si procede per livelli si vede che il nodo goal è almeno sullo stesso livello di quello che si sta esplorando
- _Strategia ottimale_ se gli operatori hanno tutti lo _stesso costo_ $k$, cioè $g(n) = k · depth(n)$, dove $g(n)$ è il costo del cammino per arrivare a $n$ 
-  _[[Complessita]] nel tempo_ (nodi generati) $T(b, d) = 1+ b + b^2 + \dots + b^d\rightarrow O(b^d)$  
 >[!nota]
> Riflettere che il numero nodi cresce exp., non assumiamo di conoscere già il grafo ne una notazione di linearità nel numero nodi . Questo è tipico dei problemi in AI (pensate a quelli generati per le configurazioni dei giochi, con rappresentazione implicita dello spazio stati, non esplicitamente/staticamente in spazi enormi). 
- _[[Complessita]] spazio_ (nodi in memoria): $O(b^d )$ _frontiera_ e $O(b^{d-1})$ per _esplorati_

>[!warning]
>Se il test goal fosse stato fatto al espansione e non alla generazione la complessita in spazio per la frontiera e in tempo sarebbe stata $O(b^{d+1})$

![[Pasted image 20230212011517.png]]
Il problema in questo caso è lo spazio che cresce troppo in fretta