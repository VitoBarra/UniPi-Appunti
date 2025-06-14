---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Inferenza logica - Algoritmo di risoluzione per PL 
---
L'[[Algoritmi|algoritmo]] **PL** ([[Logica proposizionale|propositional logic]]) è un algoritmo di [[Sistemi di inferenza logica|inferenza logica ]] che si basa sulla [[Dimostrazione di Teoremi per assurdo o contraddizione|dimostrazione per contraddizione]], secondo cui per provare che $KB \models \alpha$ è sufficiente mostrare che l **enunciato** $KB \land \neg \alpha$ è **[[Logica|insoddisfacibile]]**. 

L'algoritmo prende in input enunciati espressi in [[Logica proposizionale|logica proposizionale]] e in [[Forma normale congiuntiva (CNF)|forma normale congiuntiva (CNF)]] e si basa sull'applicazione ripetuta della [[Inferenza logica per dimostrazione di teoremi|regola di risoluzione]] finché non si arriva ad uno di questi due casi: 
1. l’impossibilità di generare ulteriori clausole, il che implica che $KB \not\models \alpha$
2. la derivazione della clausola vuota, che corrisponde a $Falso$ e quindi vale $KB \land \neg \alpha \equiv Falso$ e quindi $KB \models \alpha$.
   
Alcuni passaggi, pur formalmente corretti, risultano ridondanti: ad esempio una clausola del tipo $B_{1,1} \lor \neg B_{1,1} \lor P_{1,2}$ equivale a $Vero$ e pertanto può essere scartata senza perdita di informazione.

lo pseudo codice del algoritmo è il seguente:
```pseudo
\begin{algorithm}
\caption{PL-RESOLUTION($KB, \alpha$) returns true or false}
\begin{algorithmic}
\STATE \textbf{inputs:} $KB$, the knowledge base, a sentence in propositional logic
\STATE $\alpha$, the query, a sentence in propositional logic
\STATE clauses $\leftarrow$ the set of clauses in the CNF representation of $KB \land \neg \alpha$
\STATE new $\leftarrow \{\}$
\WHILE{true}
    \FOR{each pair of clauses $C_i, C_j$ in clauses}
        \STATE resolvents $\leftarrow$ PL-RESOLVE($C_i, C_j$)
        \IF{resolvents contains the empty clause}
            \RETURN true
        \ENDIF
        \STATE new $\leftarrow$ new $\cup$ resolvents
    \ENDFOR
    \IF{new $\subseteq$ clauses}
        \RETURN false
    \ENDIF
    \STATE clauses $\leftarrow$ clauses $\cup$ new
\ENDWHILE
\end{algorithmic}
\end{algorithm}
```


La nozione di **chiusura per risoluzione** $RC(S)$ permette di caratterizzare l’intero insieme delle clausole che possono essere generate a partire da un insieme iniziale $S$ applicando ripetutamente la regola di risoluzione. In altri termini, $RC(S)$ è definito come l’insieme di tutte le clausole derivabili da $S$, includendo sia le clausole originarie sia quelle ottenute per successive risoluzioni. Poiché l’universo dei simboli proposizionali è finito e il processo di fattorizzazione elimina duplicati e ridondanze, anche $RC(S)$ risulta finito. Da ciò segue che la procedura di risoluzione termina sempre, dato che non è possibile produrre indefinitamente nuove clausole distinte.

La **completezza** della risoluzione afferma che se un insieme di clausole è insoddisfacibile, allora dalla sua chiusura per risoluzione si ottiene necessariamente la clausola vuota. La dimostrazione procede assumendo l’opposto: supponiamo che la clausola vuota non compaia in $RC(S)$. In questo caso, $S$ non può essere insoddisfacibile, dunque deve essere soddisfacibile. Per mostrarlo si costruisce direttamente un modello, cioè un’assegnazione di valori di verità ai simboli proposizionali $P_1, \dots, P_k$. L’assegnazione è definita in sequenza: per ciascun simbolo $P_i$, se in $RC(S)$ compare una clausola che contiene $\neg P_i$ e in cui tutti gli altri letterali sono già valutati come Falso, allora $P_i$ viene assegnato a Falso; in ogni altro caso $P_i$ viene assegnato a Vero. Con questa procedura nessuna clausola di $RC(S)$ può risultare falsificata. Infatti, se accadesse che una clausola divenisse falsa, significherebbe che per $P_i$ erano presenti in $RC(S)$ contemporaneamente sia una clausola che lo richiedeva vero sia una che lo richiedeva falso, e il loro risolvente sarebbe stato già incluso in $RC(S)$, contraddicendo l’ipotesi di partenza. Di conseguenza l’assegnazione ottenuta è un modello valido per l’intera chiusura $RC(S)$ e, dato che $S$ è contenuto in $RC(S)$, lo è anche per $S$ stesso. Questa costruzione dimostra che, in assenza della clausola vuota, l’insieme è soddisfacibile, e quindi il teorema risulta provato.
