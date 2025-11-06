---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - IIA
  - AIF
topic: nota
---
# Ricerca Local beam
---
La **Ricerca Local beam** è un [[Algoritmi|algoritmo]] appartenente alla classe della [[Ricerca locale|ricerca locale]], e rappresenta una variante della [[Ricerca Beam|Ricerca beam]], mantiene quindi $k$ stati contemporaneamente in memoria. Il processo inizia con la generazione casuale di $k$ stati iniziali. Ad ogni iterazione, vengono generati tutti i successori di questi $k$ stati. Se uno dei successori rappresenta uno stato goal, la ricerca termina immediatamente. In caso contrario, si selezionano i $k$ migliori successori tra tutti quelli generati, basandosi sulla funzione di valutazione definita per il problema, e si procede ripetendo il processo.

Una caratteristica distintiva della ricerca Local beam rispetto a semplici approcci multi-start, come il [[Ricerca Hill Climbing|random-restart hill climbing]], è lo scambio di informazioni tra i vari percorsi di ricerca. I rami più promettenti attirano gli altri, concentrando gradualmente l'esplorazione nelle regioni più favorevoli dello spazio degli stati, secondo una sorta di meccanismo collaborativo in cui gli stati migliori guidano l'intera popolazione.

Tuttavia, questa strategia può portare a una perdita di diversità: i $k$ stati possono facilmente convergere in un'area ristretta dello spazio delle soluzioni, rendendo la ricerca poco efficace e simile ad una semplice [[Ricerca Hill Climbing|hill climbing]] moltiplicata per $k$. Per mitigare questo rischio, viene introdotta una variante denominata **ricerca stochastic beam**, analoga alla [[Ricerca Hill Climbing|salita stocastica della collina]].

In questa versione, i successori non vengono selezionati esclusivamente in base al valore massimo della funzione obiettivo. Invece, ogni successore ha una probabilità di essere scelto proporzionale al proprio valore. Se indichiamo con $v_i$ il valore del successore $i$ e con $V = \sum_j v_j$ la somma dei valori di tutti i successori generati, la probabilità di selezione del successore $i$ sarà:

$$
P(i) = \frac{v_i}{V}
$$

Questa introduzione di casualità controllata consente di mantenere una maggiore diversificazione tra i cammini di ricerca, riducendo il rischio di prematura convergenza verso ottimi locali e migliorando l’esplorazione globale dello spazio delle soluzioni.
