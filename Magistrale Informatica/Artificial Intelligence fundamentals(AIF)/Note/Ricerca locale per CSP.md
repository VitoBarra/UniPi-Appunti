---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca locale per CSP
---
La ricerca locale si rivela particolarmente efficace nella risoluzione dei problemi di soddisfacimento di vincoli (CSP). Questa categoria di algoritmi opera su una formulazione a stato completo, nella quale ogni stato rappresenta un'assegnazione completa di valori alle variabili del problema. L'evoluzione della ricerca si basa su modifiche incrementali, variando il valore di una singola variabile alla volta, con l'obiettivo di ridurre progressivamente le violazioni dei vincoli.

Il problema delle 8 regine può essere trattato come un CSP, con ogni colonna che rappresenta una variabile e le righe i possibili valori. L'approccio si basa sul selezionare casualmente una variabile in conflitto e modificarne il valore per ridurre il numero complessivo di conflitti, utilizzando l'euristica denominata *min-conflicts*. Tale strategia prevede la scelta della configurazione che minimizza le violazioni, procedendo iterativamente finché non si raggiunge una configurazione priva di conflitti.

Il metodo *min-conflicts* si distingue per l'efficacia su CSP di varia complessità. È stato osservato che, per problemi come $n$-queens, il tempo medio per trovare una soluzione, esclusa l'assegnazione iniziale, rimane pressoché costante al variare della dimensione $n$. Persino per il caso limite del problema con un milione di regine, la soluzione viene ottenuta in circa 50 passaggi, fenomeno che ha stimolato numerosi studi sulla complessità dei problemi e sull'efficienza degli algoritmi di ricerca locale.

Tale efficienza deriva dalla distribuzione densa delle soluzioni nello spazio degli stati, che agevola la convergenza. Tuttavia, anche per problemi più complessi, la strategia si dimostra efficace, come evidenziato dall'applicazione alla pianificazione delle osservazioni per il telescopio spaziale Hubble, dove i tempi di pianificazione sono stati ridotti drasticamente.

Le tecniche di [[Ricerca locale]] si adattano bene ai CSP grazie alla possibilità di esplorare lo spazio degli stati attraverso movimenti locali. L'euristica *min-conflicts* genera spesso paesaggi con ampi altipiani, ovvero regioni in cui molte configurazioni presentano lo stesso numero di conflitti. In tali contesti, le strategie di ricerca devono essere raffinate per evitare stalli.

Una prima soluzione è la ricerca su altipiano, che consente mosse laterali verso stati con punteggio equivalente. Questo approccio può essere ottimizzato mediante il *tabu search*, che introduce una memoria delle configurazioni visitate recentemente, impedendo cicli e favorendo l'esplorazione di nuove regioni dello spazio degli stati.

Tecniche come la [[Ricerca Simulated Annealing]] si rivelano utili per superare le trappole degli altipiani, introducendo una componente probabilistica che consente transizioni verso stati peggiori in modo controllato, favorendo la diversificazione.

Un ulteriore affinamento della ricerca locale si ottiene con il *constraint weighting*, che attribuisce pesi numerici ai vincoli, inizialmente impostati a 1. Durante l'esecuzione, i pesi dei vincoli violati vengono incrementati, influenzando la selezione delle variabili e dei valori da modificare. Questo meccanismo introduce una topografia artificiale sugli altipiani e un processo di apprendimento che penalizza i vincoli più problematici, indirizzando la ricerca verso le aree più complesse della soluzione.

La ricerca locale trova applicazione anche in contesti dinamici e online, dove le condizioni del problema possono mutare. Ad esempio, nella pianificazione di voli aerei, eventi imprevisti come condizioni meteorologiche avverse possono invalidare la soluzione corrente. In tali casi, la ricerca locale consente di riparare la soluzione esistente con modifiche minime, risultando più efficiente rispetto a una nuova ricerca esaustiva, che potrebbe richiedere tempi prolungati e generare soluzioni radicalmente diverse.


```pseudo

\begin{algorithm}
\caption{Min-Conflicts for CSP}
\begin{algorithmic}

\FUNCTION{MIN-CONFLICTS}{csp, max\_steps} \COMMENT{Returns a solution or failure}
    \STATE \textbf{inputs:} \\
    \STATE \hspace{1em} $csp$, a constraint satisfaction problem \\
    \STATE \hspace{1em} $max\_steps$, the number of steps allowed before giving up
    \STATE $current \gets$ an initial complete assignment for $csp$
    
    \FOR{$i = 1$ to $max\_steps$}
        \IF{$current$ is a solution for $csp$}
            \RETURN $current$
        \ENDIF
        \STATE $var \gets$ a randomly chosen conflicted variable from $csp.VARIABLES$
        \STATE $value \gets$ the value $v$ for $var$ that minimizes \CALL{CONFLICTS}{$csp$, $var$, $v$, $current$}
        \STATE set $var = value$ in $current$
    \ENDFOR
    \RETURN failure
\ENDFUNCTION

\end{algorithmic}
\end{algorithm}
```