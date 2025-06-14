---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con bayesian network - Enumerazione
---
L’**[[Inferenza con bayesian network| inferenza con bayesian network]] per enumerazione** si basa sulla valutazione esplicita delle probabilità condizionate tramite la somma sui valori delle variabili nascoste, ricostruendo implicitamente la distribuzione congiunta completa. Data una query $P(X \mid e)$, si utilizza la relazione $P(X \mid e) = \alpha P(X, e) = \alpha \sum_y P(X, e, y)$, dove $\alpha$ è un fattore di normalizzazione e $y$ rappresenta l’insieme delle variabili non osservate. si applica poi la semantica della [[Bayesian network|rete bayesiana]] cosi da riscrive ciascun termine come prodotto di [[Probabilita condizionata|probabilità condizionate]] tratte dalle tabelle CPT. 

L’algoritmo **ENUMERATION-ASK** implementa questa procedura in modo ricorsivo, eseguendo una [[Ricerca in profondita (DF)|ricerca in profondità]] da sinistra verso destra. Ogni chiamata valuta i prodotti dei fattori $P(v\mid parents(V))$ per le variabili della rete, estendendo progressivamente l’insieme delle evidenze e sommando sui valori possibili delle variabili non osservate. La struttura di calcolo corrisponde a un albero di valutazione in cui le somme e i prodotti riflettono la decomposizione della distribuzione congiunta in termini di dipendenze locali.
```pseudo
\begin{algorithm}
\caption{Enumeration Ask}
\begin{algorithmic}
\Function{ENUMERATION-ASK}{X, e, bn}
    \State \textbf{returns} a distribution over X
    \State \textbf{inputs:} $X$, the query variable
    \State  $e$, observed values for variables E
    \State  $bn$, a Bayes net with variables vars
    \State $Q(X) \gets$ a distribution over $X$, initially empty
    \For{each value $x_i$ of $X$}
        \State $Q(x_i) \gets$ \Call{ENUMERATE-ALL}{vars, $e_{x_i}$}
        \State  where $e_{x_i}$ is extended with $X = x_i$
    \EndFor
    \Return \Call{NORMALIZE}{$Q(X)$}
\EndFunction
\State
\Function{ENUMERATE-ALL}{vars, e}
    \State \textbf{returns} a real number
    \If{\Call{EMPTY?}{vars}}
        \Return 1.0
    \EndIf
    \State $V \gets$ \Call{FIRST}{vars}
    \If{$V$ is an evidence variable with value $v$ in $e$}
		\Return $P(v\mid parents(V)) \times$ \Call{ENUMERATE-ALL}{\Call{REST}{vars}, e}
    \Else
        \Return $\sum_v P(v \mid parents(V)) \times$ \Call{ENUMERATE-ALL}{\Call{REST}{vars}, $e_v$}
        \State  where $e_v$ is extended with $V = v$
    \EndIf
\EndFunction
\end{algorithmic}
\end{algorithm}
```
![[IMG - evaluation tree Inferenza con bayesian network.png]]
Il processo computa tutte le combinazioni rilevanti delle variabili, ma senza costruire esplicitamente l’intera distribuzione, ottenendo così una complessità spaziale lineare rispetto al numero di variabili. Tuttavia, la [[Complessita|complessità temporale]] resta esponenziale $O(2^n)$ a causa delle somme su tutte le configurazioni delle variabili non evidenziate.


