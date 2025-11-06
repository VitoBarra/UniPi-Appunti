---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Algoritmo Forward and Backward chaining per Dimostrazione di teoremi
---
l'algoritmo ***forward chaining*** per la [[dimostrazione di teoremi tramite ricerca|dimistrazioni di teoremi tramite ricerca]]. Si vuole decidere se $KB \models q$ ovvero se un [[Logica proposizionale|simbolo proposizionale]] $q$ (query) è [[Conseguenza Logica (Deduzione)|conseguenza logica]] di una base di conoscenza $KB$ fatta da sole [[Forma a Clausola definita e Clausola di Horn|clausole definite]]. 
L'algoritmo parte dai fatti noti nella $KB$ e, qualora tutte le premesse di una implicazione risultino soddisfatte, ne aggiunge la conclusione all'insieme delle conoscenze. Il processo prosegue finché non si deduce il simbolo $q$ o finché non si possono trarre ulteriori conclusioni.

Il funzionamento si comprende osservando un grafo [[Alberi di ricerca AND-OR|AND–OR]], dove le foglie rappresentano i fatti noti e i rami logici mostrano la propagazione dell'informazione. Gli archi congiuntivi richiedono che tutte le condizioni siano soddisfatte prima di procedere all'inferenza.

![[IMG - PT-ForwardChaining.png]]

Ogni passo del **forward chaining** applica il principio del ***[[Inferenza logica per dimostrazione di teoremi|Modus Ponens]]***, garantendo la correttezza (*soundness*) dell'algoritmo. La completezza si verifica analizzando lo stato finale, in cui ogni simbolo inferito è vero e gli altri sono considerati falsi. Tale configurazione può essere vista come un modello logico. Qualora una clausola del tipo $a_1 \land a_2 \land \dots \land a_k \Rightarrow b$ risultasse falsa nel modello, tutte le premesse $a_1, \dots, a_k$ dovrebbero essere vere e $b$ falso, contraddicendo il presupposto che l'algoritmo abbia raggiunto un punto fisso. Di conseguenza, l'insieme dei simboli inferiti definisce un modello della base originale e ogni simbolo $q$ entailed dalla base deve essere presente nell'insieme inferito.

```pseudo
\begin{algorithm}
\caption{PL-FC-ENTAILS?}
\begin{algorithmic}

\REQUIRE $KB$: base di conoscenza, insieme di clausole definite proposizionali \\
\REQUIRE $q$: query, un simbolo proposizionale
\ENSURE \texttt{true} se $KB \models q$, \texttt{false} altrimenti

\Function{PL-FC-ENTAILS?}{KB, q}
\STATE $count \leftarrow$ tabella, dove $count[c]$ è inizialmente il numero di simboli nella premessa della clausola $c$
\STATE $inferred \leftarrow$ tabella, inizialmente \texttt{false} per tutti i simboli
\STATE $queue \leftarrow$ coda di simboli, inizialmente simboli noti come veri in $KB$

\WHILE{$queue$ non è vuota}
    \STATE $p \leftarrow \text{Pop}(queue)$
    \IF{$p = q$}
        \RETURN \texttt{true}
    \ENDIF
    \IF{$inferred[p] = \texttt{false}$}
        \STATE $inferred[p] \leftarrow \texttt{true}$
        \FORALL{clausola $c$ in $KB$ dove $p$ è nella premessa di $c$}
            \STATE decrementa $count[c]$
            \IF{$count[c] = 0$}
                \STATE aggiungi $c.\text{CONCLUSION}$ a $queue$
            \ENDIF
        \ENDFOR
    \ENDIF
\ENDWHILE

\RETURN \texttt{false}
\EndFunction
\end{algorithmic}
\end{algorithm}

```
Il **forward chaining** un algoritmo **guidato dai dati*** (***data-driven reasoning***), dove l'inferenza parte dai dati noti senza che vi sia necessariamente una domanda esplicita. 

L'***backward chaining***, invece, opera partendo dall'obiettivo. Se il simbolo $q$ richiesto è noto, il procedimento si arresta. Altrimenti, si cercano nel $KB$ tutte le implicazioni che hanno come conclusione $q$; se le premesse possono essere verificate ricorsivamente, allora $q$ è vero.

La procedura segue una logica di *ragionamento orientato agli obiettivi* (*goal-directed reasoning*), che si rivela efficiente per rispondere a interrogativi specifici, minimizzando il numero di fatti da esaminare rispetto all'intera base di conoscenza.

Nella struttura grafica corrispondente, il **backward chaining** si traduce nella risalita dal simbolo-obiettivo attraverso i rami logici, fino a raggiungere le foglie, cioè i fatti noti, necessari per la validità della deduzione.

