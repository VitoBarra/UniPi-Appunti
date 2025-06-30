# Forwarding and Backward chaining per Dimostrazione di teoremi
## Horn Clauses and definite clauses
Alcune restrizioni sulla base di conoscenza permmettono l'adozione di algoritmi di inferenza più efficienti.
***clausola definita***: ovvero una disgiunzione di letterali in cui esattamente uno è positivo.
***clausola di Horn***: più generale della ***clausola definita***, che consente al massimo un letterale positivo ma accetta anche clausole con zero letterali positiv. 
Ogni clausola definita è dunque un caso particolare di clausola di **Horn**, mentre le clausole prive di letterali positivi vengono denominate ***clausole obiettivo*** (*goal clauses*).

Le clausole di Horn risultano [[Operazioni chiuse|chiuse]] rispetto all'[[Inferenza logica per dimostrazione di teoremi|operazione di risoluzione]]: la combinazione di due clausole di Horn tramite risoluzione produce nuovamente una clausola di Horn. Inoltre, 

si introduce il concetto di *k-CNF*, ovvero una formula in forma normale congiuntiva in cui ogni clausola contiene al massimo $k$ letterali.


ogni **clausola definita** può essere riscritta come [[Logica proposizionale|implicazione]] con un corpo (***body***) costituito da una congiunzione di letterali positivi e una testa (***head***) rappresentata da un singolo letterale positivo. Formalmente, una clausola come $(\neg P_1 \lor \neg P_2 \lor P_3)$ si traduce nell'implicazione $(P_1 \land P_2) \Rightarrow P_3$. gli **anunciati** composte da un singolo letterale positivo, dette *fatti* (*facts*), corrispondono ad implicazioni in cui la premessa è semplicemente $True$, ma per semplicità si omette tale formalizzazione.

### Algoritmo


Nel metodo di ***forward chaining***, si verifica se un simbolo proposizionale $KB \models q$. L'algoritmo parte dai fatti noti e, qualora tutte le premesse di una implicazione risultino soddisfatte, ne aggiunge la conclusione all'insieme delle conoscenze. Il processo prosegue finché non si deduce il simbolo $q$ o finché non si possono trarre ulteriori conclusioni.

Il funzionamento si comprende osservando un grafo [[Alberi di ricerca AND-OR|AND–OR]], dove le foglie rappresentano i fatti noti e i rami logici mostrano la propagazione dell'informazione. Gli archi congiuntivi richiedono che tutte le condizioni siano soddisfatte prima di procedere all'inferenza.

Ogni passo del **forward chaining** applica il principio del *Modus Ponens*, garantendo la correttezza (*soundness*) dell'algoritmo. La completezza si verifica analizzando lo stato finale, in cui ogni simbolo inferito è vero e gli altri sono considerati falsi. Tale configurazione può essere vista come un modello logico. Qualora una clausola del tipo $a_1 \land a_2 \land \dots \land a_k \Rightarrow b$ risultasse falsa nel modello, tutte le premesse $a_1, \dots, a_k$ dovrebbero essere vere e $b$ falso, contraddicendo il presupposto che l'algoritmo abbia raggiunto un punto fisso. Di conseguenza, l'insieme dei simboli inferiti definisce un modello della base originale e ogni simbolo $q$ entailed dalla base deve essere presente nell'insieme inferito.

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



Il forward chaining rappresenta un paradigma di *ragionamento guidato dai dati* (*data-driven reasoning*), dove l'inferenza parte dai dati noti senza che vi sia necessariamente una domanda esplicita. Questo approccio si integra bene con agenti logici, che possono aggiornare dinamicamente la propria base di conoscenza e trarre nuove conclusioni al ricevimento di nuovi percetti.

L'*algoritmo di backward chaining*, invece, opera partendo dall'obiettivo. Se il simbolo $q$ richiesto è noto, il procedimento si arresta. Altrimenti, si cercano nel $KB$ tutte le implicazioni che hanno come conclusione $q$; se le premesse possono essere verificate ricorsivamente, allora $q$ è vero.

La procedura segue una logica di *ragionamento orientato agli obiettivi* (*goal-directed reasoning*), che si rivela efficiente per rispondere a interrogativi specifici, minimizzando il numero di fatti da esaminare rispetto all'intera base di conoscenza.

Nella struttura grafica corrispondente, il backward chaining si traduce nella risalita dal simbolo-obiettivo attraverso i rami logici, fino a raggiungere le foglie, cioè i fatti noti, necessari per la validità della deduzione.

