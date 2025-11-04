---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
Area: 
SubTopic:
---

# Ricerca Simulated Annealing
---
L'algoritmo di **Simulated Annealing** è una tipo di [[Ricerca locale|ricerca locale]] che adotta una scelta del prossimo modo in modo [[Definizione di Probabilita|stocastico]], si fa con l ottima di combinare la completezza un **random walk** e l efficienza di fare una scelta sensata.

per fare ciò 
Ad ogni passo, l'algoritmo seleziona casualmente un successore $n'$. indicando con  $\Delta E = f(n') - f(n)$ la variazione di qualità dello stato;  Se 
- $\Delta E>0$ allora il nuovo stato $n'$ migliora la valutazione rispetto allo stato corrente $n$ e viene immediatamente accettato. 
- $\Delta E\leq 0$ allora il nuovo stato $n'$ __non risulta migliore__, ma puo comunque essere accettato con una certa [[Definizione di Probabilita|probabilita]] definita dalla [[Distribuzione di Boltzmann|distribuzione di Boltzmann]]: $p =\alpha e^{\Delta E / kT}$ dove $T$ è un parametro detto **temperatura**, che decresce progressivamente durante l'esecuzione dell'algoritmo, secondo un piano di raffreddamento prestabilito.

Questa formulazione consente che la probabilità $p$ sia inversamente proporzionale al peggioramento: quando $\Delta E$ . In tal modo, all'inizio dell'esecuzione, quando $T$ è elevata, l'algoritmo è più incline ad accettare mosse peggiorative, favorendo l'esplorazione dello spazio di ricerca e la possibilità di superare massimi locali. Con il progressivo abbassamento della temperatura, la dinamica tende gradualmente ad avvicinarsi al comportamento deterministico proprio della [[Ricerca Hill Climbing|Hill climbing]].

I valori iniziali e il piano di decremento della temperatura vengono generalmente determinati in maniera _sperimentale_. In particolare, il valore iniziale di $T$ viene scelto affinché, per variazioni medie di $\Delta E$, la probabilità $p = e^{\Delta E / T}$ assuma inizialmente un valore approssimativamente prossimo a $0.5$.

se $T$ viene abbassato abbastanza lentamente allora è garantito che verra trovata una soluzione ottima

una versione pseudo codice:
```pseudo
	\begin{algorithm}
	\caption{simulated annealing}
\begin{algorithmic}
\Function{SIMULATED-ANNEALING}{problem, schedule}
    \State $\text{current} \gets \text{problem.INITIAL}$
    \For{$t = 1$ \textbf{to} $\infty$}
        \State $T \gets \text{schedule}(t)$
        \If{$T = 0$}
            \Return current
        \EndIf
        \State $\text{next} \gets \text{a randomly selected successor of current}$
        \State $\Delta E \gets \text{VALUE(current)} - \text{VALUE(next)}$
        \If{$\Delta E > 0$}
            \State $\text{current} \gets \text{next}$
        \Else
            \State $\text{current} \gets \text{next}$ only with probability $e^{-\Delta E / T}$
        \EndIf
    \EndFor
\EndFunction
\end{algorithmic}
	\end{algorithm}
```



