---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - IIA
  - AIF
topic: "[[Problemi di ricerca]]"
---

# Ricerca Generativa-Evolutiva
---
La **Ricerca Generativa-Evolutiva** è un tipo di [[Ricerca locale|ricerca locale]], strettamente imparentata con la [[Ricerca Local beam#Versione stocastica|Beam search stocastica]]. Essa si ispira al principio biologico della selezione naturale, dove una popolazione di individui evolve nel tempo attraverso selezione, riproduzione e mutazione. Gli stati successori vengono generati combinando il materiale genetico di due stati genitori selezionati.

Inizialmente viene generata una popolazione casuale di $k$ individui, ciascuno rappresentato da una stringa o da altre strutture a seconda della variante specifica. La rappresentazione scelta è cruciale, poiché influisce sulla capacità dell’algoritmo di individuare e combinare sotto-strutture significative.

Ogni individuo viene valutato tramite una **_funzione di fitness_**, che assegna un punteggio in funzione della qualità della soluzione rappresentata. La selezione dei genitori avviene con probabilità proporzionale alla fitness, favorendo gli individui più promettenti. In alternativa, è possibile adottare selezioni più complesse, come il 
- **_tournament selection_**, in cui un sottoinsieme casuale di individui compete per la riproduzione.
- **elitism**: un certo numero dei migliori individui viene passato direttamente alla prossima generazione cosi come sono per non perdere buone soluzioni.

Le coppie selezionate danno origine alla nuova generazione attraverso il meccanismo del _crossover_. Per ogni coppia viene scelto casualmente un punto di crossover, che divide le stringhe parentali in due segmenti. I figli vengono generati combinando i segmenti corrispondenti: il primo figlio eredita la prima parte del primo genitore e la seconda parte del secondo, mentre il secondo figlio eredita l’opposto. Questo consente il riuso e la combinazione di sottostrutture vantaggiose.

![[IMG - Ricerca Generativa-Evolutiva esempio 8 regine.png]]

A seguito del crossover, ogni gene nelle stringhe figli può subire una mutazione casuale, con una piccola probabilità definita dal **_mutation rate_**. 

uno pseudo codice è il seguente:
```pseudo
\begin{algorithm}
\caption{genetic algorithm}
\begin{algorithmic}
\Function{GENETIC-ALGORITHM}{population, fitness}
    \Repeat
        \State $\text{weights} \gets \text{WEIGHTED-BY}(\text{population}, \text{fitness})$
        \State $\text{population2} \gets \text{empty list}$
        \For{$i = 1$ \textbf{to} $\text{SIZE}(\text{population})$}
            \State $\text{parent1}, \text{parent2} \gets \text{WEIGHTED-RANDOM-CHOICES}(\text{population}, \text{weights}, 2)$
            \State $\text{child} \gets \text{REPRODUCE}(\text{parent1}, \text{parent2})$
            \If{$\text{small random probability}$}
                \State $\text{child} \gets \text{MUTATE}(\text{child})$
            \EndIf
            \State $\text{add child to population2}$
        \EndFor
        \State $\text{population} \gets \text{population2}$
    \Until{$\text{some individual is fit enough, or enough time has elapsed}$}
    \Return $\text{the best individual in population, according to fitness}$
\EndFunction
\State
\Function{REPRODUCE}{parent1, parent2}
    \State $n \gets \text{LENGTH}(\text{parent1})$
    \State $c \gets \text{random number from } 1 \text{ to } n$
    \Return $\text{APPEND}(\text{SUBSTRING}(\text{parent1}, 1, c), \text{SUBSTRING}(\text{parent2}, c + 1, n))$
\EndFunction
\end{algorithmic}
\end{algorithm}
```

Con il susseguirsi delle generazioni, la fitness media tende a crescere progressivamente, poiché i migliori schemi (o _schema_) si propagano. Uno _schema_ è una sottostringa parzialmente definita, come $246*****$, che rappresenta tutte le configurazioni con le prime tre regine nelle posizioni 2, 4 e 6. Se la fitness media degli individui che rispettano uno schema supera la media della popolazione, la frequenza dello schema aumenta nel tempo. Questo processo permette l’amplificazione di blocchi funzionali che costituiscono buoni componenti parziali della soluzione complessiva.