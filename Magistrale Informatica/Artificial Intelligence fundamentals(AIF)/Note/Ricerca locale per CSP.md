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
un [[Algoritmi|algoritmo]] di  [[Ricerca locale|ricerca locale]] per [[Problemi di soddisfacibilita vincolata (CSP)]]. Questa categoria di algoritmi opera su una **formulazione a stato completo**, nella quale ogni stato rappresenta un'assegnazione completa di valori alle variabili del problema. L'evoluzione della ricerca si basa su **modifiche incrementali**, variando il valore di una singola variabile alla volta, con l'obiettivo di ridurre progressivamente le violazioni dei vincoli.

per fare ciò si utilizzando l'euristica ***min-conflicts*** che sceglie una variabile a caso tra quelli che hanno dei conflitti e per questa variabile sceglie un valore che minimizza il numero di conflitti, cosi  da minimizzare in conflitti violati dalla **formulazione completa**, procedendo iterativamente finché non si raggiunge una configurazione priva di conflitti.

```pseudo

\begin{algorithm}
\caption{Min-Conflicts for CSP}
\begin{algorithmic}

\FUNCTION{MIN-CONFLICTS}{csp, max\_steps} \COMMENT{Returns a solution or failure}
    \STATE \textbf{inputs:} \\
    \STATE  $csp$, a constraint satisfaction problem \\
    \STATE  $max\_steps$, the number of steps allowed before giving up
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

Le tecniche di [[Ricerca locale]] si adattano bene ai [[Problemi di soddisfacibilita vincolata (CSP)|CSP]] grazie alla possibilità di esplorare lo spazio degli stati attraverso movimenti locali. L'euristica *min-conflicts* genera spesso paesaggi con ampi platou, ovvero regioni in cui molte configurazioni presentano lo stesso numero di conflitti. In tali contesti, le strategie di ricerca devono essere raffinate per evitare stalli.

Una prima soluzione è consentire mosse laterali verso stati con punteggio equivalente. Questo approccio può essere ottimizzato mediante il ***tabu search***, che introduce una memoria delle configurazioni visitate recentemente, impedendo cicli e favorendo l'esplorazione di nuove regioni dello spazio degli stati.

Tecniche come la [[Ricerca Simulated Annealing]] si rivelano utili per superare le trappole degli altipiani, introducendo una componente probabilistica che consente transizioni verso stati peggiori in modo controllato, favorendo la diversificazione.

Un ulteriore affinamento della ricerca locale si ottiene con il ***constraint weighting***, che attribuisce pesi numerici ai vincoli, inizialmente impostati a $1$. Durante l'esecuzione, i pesi dei vincoli violati vengono incrementati, influenzando la selezione delle variabili e dei valori da modificare. Questo meccanismo introduce una topografia artificiale sugli altipiani e un processo di apprendimento che penalizza i vincoli più problematici, indirizzando la ricerca verso le aree più complesse della soluzione.