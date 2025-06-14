---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
---

# Ricerca in ampiezza (BF)
---
la **Ricerca in ampiezza** o **Breadth-first search** (BF) è un [[Algoritmi di ricerca non informati|Algoritmo di ricerca]] che utilizza una [[Coda (FIFO)|coda FIFO]] per implementare la **frontiera**, si assume che il costo di ogni arco è $1$.
Il controllo del raggiungimento del nodo goal è fatto al momento della **generazione** dei nodi (**early goal test**) e non al momento del esplorazione (**late goal test**), questo riduce la [[Complessita|complessità]]

 Per la  **BF** sia su [[grafi|grafi]] che su [[Alberi|alberi]] genera i nodi a profondità $d$ solo dopo aver generato tutti i nodi profondità $d-1$ e per questo si diche che esplora con **profondità uniforme**.  Per questa proprietà usa sempre un numero minimo di azioni per trovare il goal.
 
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

- **completa**: se $b$ è **finito** non vengono lasciate strade non esplorate siccome si procede per livelli
- **NON completo**: se $b$ è **infinito** in quando resterebbe bloccato sul esplorazione del primo livello 
- **Ottimalità** se gli operatori hanno tutti lo **_stesso costo_** $k$, cioè $g(n) = k · depth(n)$, dove $g(n)$ è il costo del cammino per arrivare a $n$ 
- _**[[Complessita|Complessità nel tempo]]**_ (nodi generati) $T(b, d) = 1+ b + b^2 + \dots + b^d\rightarrow O(b^d)$  
- **_[[Complessita| Complessità in spazio]]_** (nodi in memoria): $O(b^d )$ _frontiera_ e $O(b^{d-1})$ per _esplorati_

>[!warning]
>Se il test goal fosse stato dopo il pop e non al espansione la complessit in spazio per la frontiera e in tempo sarebbe stata $O(b^{d+1})$

| Depth | Nodes     | Time             | Memory         |
| ----- | --------- | ---------------- | -------------- |
| $2$   | $110$     | .11 milliseconds | 107 kilobytes  |
| $4$   | $11,110$  | 11 milliseconds  | 10.6 megabytes |
| $6$   | $10^{6}$  | 1.1 seconds      | 1 gigabyte     |
| $8$   | $10^{8}$  | 2 minutes        | 103 gigabytes  |
| $10$  | $10^{10}$ | 3 hours          | 10 terabytes   |
| $12$  | $10^{12}$ | 13 days          | 1 petabyte     |
| $14$  | $10^{14}$ | 3.5 years        | 99 petabytes   |
| $16$  | $10^{16}$ | 350 years        | 10 exabytes    |
Il problema in questo caso è lo spazio che cresce troppo in fretta