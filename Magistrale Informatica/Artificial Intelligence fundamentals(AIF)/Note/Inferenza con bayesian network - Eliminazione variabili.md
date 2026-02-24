---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con bayesian network - Eliminazione variabili
---
L’**[[Inferenza con bayesian network| inferenza con bayesian network]] per elinimazione di variabili** si basa sulla riduzione dei calcoli ripetuti presenti nell’[[Inferenza con bayesian network - Enumerazione|approccio per enumerazione]]. L’idea centrale consiste nel calcolare una volta sola ciascuna combinazione rilevante e nel memorizzare i risultati intermedi, applicando un principio di [[programmazione dinamica|programmazione dinamica]]. valuta le espressioni dell’inferenza procedendo da destra verso sinistra, ossia dal basso verso l’alto nella struttura della rete. Ogni passaggio produce un insieme di fattori intermedi, ciascuno dei quali rappresenta una matrice indicizzata dalle variabili coinvolte.

L’espressione generale di una distribuzione condizionata, come nel caso $P(B \mid j,m)$, può essere riscritta come combinazione di fattori:
$$
P(B \mid j,m) = \alpha f_1(B) \times \sum_e f_2(E) \times \sum_a f_3(A,B,E) \times f_4(A) \times f_5(A)
$$
dove ciascun $f_i$ rappresenta un fattore costruito a partire dalle [[Probabilita condizionata|probabilità condizionate]] della rete. L’operatore “$\times$” non indica una moltiplicazione matriciale convenzionale, bensì un *prodotto punto a punto* (pointwise product) tra fattori.

```pseudo
\begin{algorithm}
\caption{Elimination Ask}
\begin{algorithmic}
\Function{ELIMINATION-ASK}{X, e, bn}
    \State \textbf{returns} a distribution over X
    \State \textbf{inputs:} $X$, the query variable
    \State  $e$, observed values for variables E
    \State  $bn$, a Bayesian network with variables vars
    \State
    \State $factors \gets [\ ]$
    \For{each $V$ in \Call{ORDER}{vars}}
        \State $factors \gets$ [\Call{MAKE-FACTOR}{V, e}] + $factors$
        \If{$V$ is a hidden variable}
            \State $factors \gets$ \Call{SUM-OUT}{V, factors}
        \EndIf
    \EndFor
    \Return \Call{NORMALIZE}{\Call{POINTWISE-PRODUCT}{factors}}
\EndFunction
\end{algorithmic}
\end{algorithm}
```
Durante la valutazione, si eliminano progressivamente le variabili non rilevanti tramite [[FJD - Marginalizzazione|somma marginale]], calcolata sui prodotti dei fattori che dipendono da esse. Si ottengono così nuovi fattori ridotti, contenenti un numero minore di variabili. La sequenza di eliminazione procede fino a produrre un unico fattore che rappresenta la distribuzione a posteriori della variabile di interesse.

Due operazioni fondamentali definiscono il funzionamento dell’algoritmo: il prodotto punto a punto e la somma di eliminazione. Il prodotto punto a punto di due fattori $f$ e $g$ genera un nuovo fattore $h$ che coinvolge l’unione delle variabili dei due fattori:
$$
f(X_1,\dots,X_j,Y_1,\dots,Y_k) \times g(Y_1,\dots,Y_k,Z_1,\dots,Z_\ell)
= h(X_1,\dots,X_j,Y_1,\dots,Y_k,Z_1,\dots,Z_\ell)
$$
Il numero di elementi del nuovo fattore cresce esponenzialmente con il numero totale di variabili coinvolte, rappresentando la principale fonte di complessità computazionale e spaziale del metodo.

L’eliminazione di una variabile da un fattore consiste nel sommare le sue proiezioni fissando la variabile a ciascun valore possibile. Se un fattore non dipende dalla variabile in esame, esso può essere portato fuori dal segno di somma, riducendo così il costo del calcolo. In termini operativi, per eliminare $X$ dal prodotto di $f$ e $g$, si sfrutta:
$$
\sum_x f(X,Y) \times g(Y,Z) = g(Y,Z) \times \sum_x f(X,Y)
$$
in modo da eseguire la moltiplicazione solo quando necessario, limitando la crescita dei fattori intermedi.

L’ordine di eliminazione delle variabili influenza in modo determinante la complessità dell’intero processo. Ogni ordine produce un algoritmo corretto, ma la dimensione massima dei fattori generati dipende dalla sequenza scelta e dalla struttura della rete. Determinare l’ordine ottimale è un problema intrattabile, ma esistono euristiche efficaci, come quella che privilegia l’eliminazione della variabile che minimizza la dimensione del fattore successivo.

Un ulteriore miglioramento deriva dall’identificazione delle variabili irrilevanti rispetto alla query. Ogni nodo foglia che non rappresenta una variabile di evidenza o di interrogazione può essere rimosso senza alterare il risultato dell’inferenza. Iterando questa procedura, si eliminano tutte le variabili che non sono antenati dei nodi rilevanti, riducendo così ulteriormente il carico computazionale. L’uso di un ordine inverso topologico nella sequenza di eliminazione consente di ottenere un’inferenza esatta con un’efficienza sensibilmente superiore rispetto al metodo di enumerazione diretta.
