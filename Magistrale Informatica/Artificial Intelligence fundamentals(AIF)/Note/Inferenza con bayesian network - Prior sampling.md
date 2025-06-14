---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con bayesian network - Prior sampling
---
Il **procedimento di inferenza approssimata** nei [[Bayesian network|Bayesian Networks]] nasce dalla necessità di gestire la complessità computazionale che rende inattuabile l’inferenza esatta in reti di grandi dimensioni. Gli algoritmi di tipo **Monte Carlo** rappresentano un insieme di metodi che mirano a stimare distribuzioni di probabilità mediante processi di **campionamento casuale**. L’accuratezza delle stime ottenute è proporzionale al numero di campioni generati. Ogni [[Variabili Aleatorie (Casuali)|variabile casuale]] $X_i$ viene campionata seguendo l’[[Ordinamento topologico|ordine topologico]] della [[Bayesian network|rete bayesiana]], così che i valori dei genitori di $X_i$ risultino già determinati al momento del sampling. La distribuzione di riferimento per il campionamento è quindi la [[probabilita condizionata|probabilita condizionata]] $P(X_i \mid parents(X_i))$. Questo processo, ripetuto per **tutte le variabili**, genera un **evento completo** $x = (x_1, \ldots, x_n)$, che rappresenta una configurazione possibile del sistema descritto dalla rete. 
in pseudo codice:
```pseudo
\begin{algorithm}
\caption{Prior Sample}
\begin{algorithmic}
\Function{PRIOR-SAMPLE}{bn}
    \State \textbf{returns} an event sampled from the prior specified by bn
    \State \textbf{inputs:} bn, a Bayesian network specifying joint distribution $\mathbf{P}(X_1, \ldots, X_n)$
    \State $x \gets$ an event with $n$ elements
    \For{each variable $X_i$ in $X_1, \ldots, X_n$}
        \State $x[i] \gets$ a random sample from $\mathbf{P}(X_i \mid parents(X_i))$
    \EndFor
    \Return $x$
\EndFunction
\end{algorithmic}
\end{algorithm}
```

La probabilità di ottenere uno specifico evento secondo l’**algoritmo di campionamento** è data da$$
S_{PS}(x_1, \ldots, x_n) = \prod_{i=1}^{n} P(x_i \mid parents(X_i)),
$$il che coincide con la semantica globale delle [[Bayesian network|Bayesian Network]]. Da ciò discende che il metodo **PRIOR-SAMPLE** produce campioni coerenti con la [[Distribuzione di probabilita congiunta totale|distribuzione congiunta]] $P(x_1, \ldots, x_n)$. 
**sia** $N$ il numero di campioni e $N_{PS}(x_1, \ldots, x_n)$ il numero  di volte che si è verificato l evento $x_1, \ldots, x_n$ **allora** possiamo [[Stimatori statistici|stimare]] la probabilità reale contando quante volte un dato evento è evento rispetto a tutti i campioni$$
\lim_{N \to \infty} \frac{N_{PS}(x_1, \ldots, x_n)}{N} = P(x_1, \ldots, x_n),
$$dove l'accuratezza della stima cresce al crescere di $N$.
Questa convergenza rende la stima $\hat{P} \approx \cfrac{N_{PS}(x_1, \ldots, x_n)}{N}$ un [[Stimatori statistici|estimatore consistente]] della distribuzione originale dove $\approx$ indica proprio il fatto che converge al aumentare di $N$. in generale questa relazione vale anche per un evento parziale definito da un sottoinsieme di variabili $x_1, \ldots, x_m$ con $m \leq n$, si ottiene$$
P(x_1, \ldots, x_m) \approx \frac{N_{PS}(x_1, \ldots, x_m)}{N}
$$