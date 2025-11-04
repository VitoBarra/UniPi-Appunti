---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Algoritmo backtracing per CSP
---
L’**algoritmo di ricerca backtracking** per i [[Problemi di soddisfacibilita vincolata (CSP)]] costituisce un metodo sistematico per esplorare le assegnazioni parziali dei valori alle variabili con l’obiettivo di individuare una soluzione che soddisfi tutti i vincoli. Al termine del processo di propagazione dei vincoli, come avviene nell’[[Algoritmo per consistenza archi AC-3]], può accadere che alcune variabili presentino domini non ridotti a un singolo valore. In tali situazioni è necessario ricorrere a una fase di ricerca esplicita.

L’analisi del problema si basa sulla corrispondenza tra uno stato e un’assegnazione parziale, dove ciascuna azione estende tale assegnazione associando un valore a una variabile. Considerando un CSP con $n$ variabili e un dominio di dimensione $d$, l’albero di ricerca raggiunge una profondità pari a $n$, corrispondente alle assegnazioni complete. Il fattore di ramificazione iniziale è pari a $nd$, decrescendo successivamente a $(n - 1)d$, $(n - 2)d$ e così via. In termini combinatori, il numero di foglie appare pari a $n! \cdot d^n$, mentre il numero effettivo di assegnazioni possibili è $d^n$.

Questa discrepanza si chiarisce osservando la proprietà di commutatività che caratterizza i CSP, per cui l’ordine delle assegnazioni non altera l’esito finale. Di conseguenza, si considera una sola variabile per ciascun livello dell’albero, evitando scelte simultanee. Tale restrizione riporta il numero di foglie al valore atteso di $d^n$.

L’algoritmo **BACKTRACKING-SEARCH**, opera modificando direttamente una singola rappresentazione dello stato corrente, in modo analogo a quanto discusso in [[Algoritmo per consistenza archi AC-3]]. Il backtracking si distingue per la possibilità di essere potenziato tramite euristiche che sfruttano la struttura fattorizzata]] dei CSP. Le principali strategie di ottimizzazione si articolano in quattro categorie: selezione della variabile da assegnare, ordinamento dei valori da provare, inferenze sui domini e tecniche avanzate di backtracking.

La scelta della variabile avviene mediante la funzione $SELECT\text{-}UNASSIGNED\text{-}VARIABLE(csp, assignment)$, che può essere basata su diverse euristiche. Un approccio semplice prevede un ordinamento statico o casuale delle variabili, ma tale criterio è subottimale. L’euristica delle **minime rimanenze di valori** (MRV, *Minimum Remaining Values*), conosciuta anche come "variabile più vincolata" o "fail-first", privilegia la variabile con il minor numero di valori legali disponibili, agevolando così l’individuazione anticipata dei fallimenti e la conseguente potatura dell’albero.

Nel caso in cui più variabili presentino lo stesso numero minimo di valori legali, si impiega l’**euristica del grado** (*Degree Heuristic*), che seleziona la variabile coinvolta nel maggior numero di vincoli con altre variabili ancora non assegnate. Tale scelta massimizza l’impatto potenziale di ogni decisione sull’intero insieme del problema.

Dopo la selezione della variabile, si stabilisce l’ordine di esplorazione dei valori attraverso l’**euristica del valore meno vincolante** (*Least Constraining Value*), che favorisce i valori in grado di restringere il meno possibile i domini delle variabili adiacenti. Questo criterio preserva la massima flessibilità per le assegnazioni successive, con una logica combinata di "fail-first" nella scelta delle variabili e "fail-last" nella selezione dei valori.

L’integrazione tra ricerca e inferenza si concretizza nell’applicazione della propagazione dei vincoli durante l’esecuzione. Il **controllo in avanti** (*Forward Checking*) verifica la consistenza degli archi ogni volta che una variabile $X$ viene assegnata, eliminando dai domini delle variabili adiacenti $Y$ i valori incompatibili con l’assegnazione di $X$. Tale operazione consente di ridurre i rami dell’albero e di identificare rapidamente eventuali contraddizioni, come illustrato nella [[Figura 6.7]]. L’efficacia dell’euristica MRV risulta amplificata se combinata con il controllo in avanti, poiché le riduzioni nei domini forniscono indicazioni immediate per individuare la prossima variabile più vincolata.

Il controllo in avanti, pur essendo utile, si limita alle relazioni immediate tra le variabili e non rileva tutte le forme di inconsistenza. Per una propagazione più completa dei vincoli si utilizza l’approccio **Maintaining Arc Consistency** (MAC), che dopo ogni assegnazione richiama l’[[Algoritmo per consistenza archi AC-3]], inizializzando la coda esclusivamente con gli archi che connettono la variabile appena assegnata alle adiacenti ancora non assegnate. Questa tecnica garantisce una potatura più incisiva dello spazio di ricerca rispetto al solo controllo in avanti, mantenendo al contempo un approccio incrementale.

Nel backtracking classico, in caso di fallimento, si ritorna cronologicamente alla variabile assegnata immediatamente prima. Una strategia più efficiente è il **Backjumping**, che consente di risalire direttamente alla variabile che ha contribuito al conflitto, individuabile mediante il cosiddetto *Conflict Set*. Tale insieme si costruisce tracciando le assegnazioni precedenti che hanno causato la rimozione di valori dai domini delle variabili, e può essere aggiornato in modo efficiente durante l’applicazione del controllo in avanti.

Una variante più avanzata è il **Conflict-Directed Backjumping**, che prende in considerazione non solo i conflitti diretti ma anche quelli che emergono da combinazioni di assegnazioni inconsistenti relative a interi sottoinsiemi di variabili. Questa tecnica si basa su un aggiornamento ricorsivo dei set di conflitto. Se una variabile $X_j$ fallisce e il suo insieme di conflitto è $conf(X_j)$, il controllo ritorna alla variabile $X_i$ più recente presente in $conf(X_j)$, aggiornando il set secondo la relazione:

$$
conf(X_i) \leftarrow conf(X_i) \cup conf(X_j) - \{X_i\}
$$

In questo modo, si percorre in modo efficiente la catena delle dipendenze, saltando rami dell’albero che non possono condurre a soluzioni.

L’ultima tecnica rilevante è l’**apprendimento dei vincoli** (*Constraint Learning*), che permette di memorizzare combinazioni di assegnazioni inconsistenti sotto forma di *no-good*, ossia insiemi minimi di variabili e valori che generano contraddizioni. I *no-good* possono essere archiviati come vincoli aggiuntivi o strutture separate, con il risultato di evitare ripetizioni nell’esplorazione dello spazio di ricerca, soprattutto nei casi caratterizzati da alta ridondanza o presenza di cicli strutturali.


```pseudo

\begin{algorithm}
\caption{Backtracking Search for CSP}
\begin{algorithmic}

\FUNCTION{BACKTRACKING-SEARCH}{csp}
    \RETURN \CALL{BACKTRACK}{csp, \{\}}
\ENDFUNCTION

\FUNCTION{BACKTRACK}{csp, assignment}
    \IF{assignment is complete}
        \RETURN assignment
    \ENDIF
    \STATE $var \gets$ \CALL{SELECT-UNASSIGNED-VARIABLE}{csp, assignment}
    \FORALL{$value$ in \CALL{ORDER-DOMAIN-VALUES}{csp, var, assignment}}
        \IF{$value$ is consistent with $assignment$}
            \STATE add $\{var = value\}$ to $assignment$
            \STATE $inferences \gets$ \CALL{INFERENCE}{csp, var, assignment}
            \IF{$inferences \neq failure$}
                \STATE add $inferences$ to $csp$
                \STATE $result \gets$ \CALL{BACKTRACK}{csp, assignment}
                \IF{$result \neq failure$}
                    \RETURN result
                \ENDIF
                \STATE remove $inferences$ from $csp$
            \ENDIF
            \STATE remove $\{var = value\}$ from $assignment$
        \ENDIF
    \ENDFOR
    \RETURN failure
\ENDFUNCTION

\end{algorithmic}
\end{algorithm}

```
