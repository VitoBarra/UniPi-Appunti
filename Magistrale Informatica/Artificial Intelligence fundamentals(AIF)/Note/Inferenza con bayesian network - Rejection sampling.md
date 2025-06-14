---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---
# Inferenza con bayesian network - rejection sampling
---
l'agloritmo ***rejection sampling*** è una **strategia generale** per campionare una [[Bayesian network|Bayesian Networks]] dove per ottenere campioni da **distribuzioni difficili** come in presenza di evidenze $e$ e vogliamo stimare $P(X \mid e)$ si parte da un’altra distribuzione più **semplice da campionare** ovvero $P(X)$ dove possiamo applicare l algoritmo di [[Inferenza con bayesian network - Prior sampling|prior sampling]]. In particolare si generano i campioni dalla distribuzione a priori e si **scartano** quelli che non **risultano coerenti** con le variabili di evidenza. I campioni accettati vengono quindi utilizzati per stimare la distribuzione condizionata, calcolata come:$$
\hat{P}(X \mid e) = \alpha \, N_{PS}(X, e) = \frac{N_{PS}(X, e)}{N_{PS}(e)}
	$$dove con $\hat{\mathcal{P}}$  si indica la [[Definizione di Probabilita|probabilita]] stimata e $N_{PS}(X, e)$ rappresenta il numero di campioni in cui la variabile $X$ assume un determinato valore compatibile con $e$, e $N_{PS}(e)$ è il numero totale di campioni accettati. Dalla relazione precedente seguendo lo stesso ragionamento per il [[Inferenza con bayesian network - Prior sampling|prior sampling]] si ottiene, in base a quanto espresso per il campionamento diretto,$$
\hat{\mathcal{P}}(X \mid e) \approx \frac{\mathcal{P}(X, e)}{\mathcal{P}(e)} = \mathcal{P}(X \mid e)
$$il che implica che la stima fornita dal ***rejection sampling*** è [[Stimatori statistici|consistente]] e converge alla probabilità reale al crescere del numero di campioni $N$. L’errore statistico associato alla stima decresce proporzionalmente a $1 / \sqrt{n}$, dove $n$ indica il numero di campioni effettivamente utilizzati.

in pseudocodice l algoritmo segue come:
```pseudo
\begin{algorithm}
\caption{Rejection Sampling}
\begin{algorithmic}
\Function{REJECTION-SAMPLING}{X, e, bn, N}
    \State \textbf{returns} an estimate of $P(X | e)$
    \State \textbf{inputs:} $X$, the query variable
    \State  $e$, observed values for variables E
    \State  $bn$, a Bayesian network
    \State  $N$, the total number of samples to be generated
    \State \textbf{local variables:} $C$, a vector of counts for each value of X, initially zero
    \State
    \For{$j = 1$ to $N$}
        \State $x \gets$ \Call{PRIOR-SAMPLE}{bn}
        \If{$x$ is consistent with $e$}
            \State $C[j] \gets C[j] + 1$ where $x_j$ is the value of $X$ in $x$
        \EndIf
    \EndFor
    \Return \Call{NORMALIZE}{C}
\EndFunction
\end{algorithmic}
\end{algorithm}
```
Tuttavia, la rapidità della convergenza è fortemente influenzata dalla **[[definizione di probabilita|probabilità]] a priori dell’evidenza** $P(e)$, che determina la frazione di campioni accettati. Nei casi in cui l’evidenza sia rara o coinvolga molte variabili, questa frazione tende a valori estremamente piccoli, riducendo drasticamente l’efficienza del metodo. Per reti complesse o con variabili continue, la probabilità di produrre un campione coerente con l’evidenza può diventare **nulla** o **trascurabile**, rendendo il **procedimento impraticabile**.

