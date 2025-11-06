---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Struttura di un CSP - Struttura ad albero
---
nei [[Problemi di soddisfacibilita vincolata (CSP)|CSP]] si può utilizzare la **struttura del problema**, rappresentata attraverso **il grafo dei vincoli**, per risolvere più velocemente il problema della ricerca di un assegnazione. il caso dove il [[Problemi di soddisfacibilita vincolata (CSP)|grafo dei vincoli]] è aciclico ovvero è ad [[Alberi|albero]]. 
La risoluzione di un [[Problemi di soddisfacibilita vincolata (CSP)|CSP]] strutturato ad albero è resa possibile attraverso la **coerenza direzionale sugli archi** (Directional Arc Consistency, DAC).


Si definisce un CSP **direzionalmente arc-consistente** rispetto ad un ordinamento delle variabili $X_1, X_2, \dots, X_n$ se ogni $X_i$ è [[Risolvere un CSP|arc-consistente]] con ogni $X_j$ tale che $j > i$.

dato un [[Grafi|grafo]] di vincoli ad [[alberi|albero]] con $n$ nodi e $n - 1$ archi dopo aver scelto un [[Ordinamento topologico|ordinamento topologico]] $X_1, X_2, \dots, X_n$ questo può essere reso **directional arc-consistente** in $O(n)$ operazioni, ciascuna richiedente al massimo $d^2$ confronti tra valori di dominio, per una complessità complessiva di $O(nd^2)$. 
Una volta garantita la coerenza direzionale, si procede nell'assegnazione dei valori in maniera sequenziale senza necessità di backtracking, data la sicurezza di disponibilità di un valore coerente per ogni variabile figlia rispetto al valore del genitore.

```pseudo
\begin{algorithm}
\caption{Tree-CSP-Solver for CSP}
\begin{algorithmic}

\FUNCTION{TREE-CSP-SOLVER}{csp} \COMMENT{Returns a solution or failure}
    \STATE \textbf{inputs:} $csp$, a CSP with components $X$, $D$, $C$
    \STATE $n \gets$ number of variables in $X$
    \STATE $assignment \gets$ an empty assignment
    \STATE $root \gets$ any variable in $X$
    \STATE $X \gets$ \CALL{TOPOLOGICALSORT}{$X$, $root$}
    
    \FOR{$j = n$ down to $2$}
        \STATE \CALL{MAKE-ARC-CONSISTENT}{PARENT($X_j$), $X_j$}
        \IF{it cannot be made consistent}
            \RETURN failure
        \ENDIF
    \ENDFOR

    \FOR{$i = 1$ to $n$}
        \STATE $assignment[X_i] \gets$ any consistent value from $D_i$
        \IF{there is no consistent value}
            \RETURN failure
        \ENDIF
    \ENDFOR

    \RETURN $assignment$
\ENDFUNCTION

\end{algorithmic}
\end{algorithm}
```

L'efficienza di questo metodo ha stimolato lo sviluppo di strategie per trasformare grafi generali in strutture ad albero. Una tecnica è il ***cutset conditioning***, che consiste nell'assegnare valori a un sottoinsieme di variabili $S$ tale che la rimozione di $S$ dal grafo generi una struttura ad albero. Tale insieme $S$ è definito *cycle cutset*. Per ogni possibile assegnazione coerente delle variabili in $S$, si eliminano dai domini delle rimanenti variabili i valori incompatibili e si risolve il sotto problema ad albero risultante. La complessità è $O(d^c \cdot (n - c)d^2)$, dove $c = |S|$. Se $c$ è sufficientemente piccolo, il miglioramento rispetto al backtracking esponenziale è sostanziale. Tuttavia, la ricerca del **cycle cutset** minimo è un problema [[Classi di complessita - NP-Hard|NP-hard]], ma esistano algoritmi approssimati efficaci.




### Tree decomposition (extra)
Un approccio alternativo è la *tree decomposition*, ovvero la trasformazione del grafo in un albero i cui nodi rappresentano insiemi di variabili. La decomposizione deve soddisfare tre requisiti: ogni variabile deve comparire almeno una volta nei nodi dell'albero, ogni coppia di variabili con vincolo diretto deve comparire insieme in almeno un nodo, e una variabile che appare in più nodi deve essere presente in ogni nodo lungo il cammino che li connette. Questa struttura garantisce la consistenza globale dei valori assegnati alle variabili replicate nei nodi.

La risoluzione del problema avviene trattando ogni nodo come una variabile i cui valori sono tuple di assegnazioni compatibili con i vincoli locali. L'algoritmo TREE-CSP-SOLVER consente di risolvere il CSP in $O(nd^2)$, con $n$ numero di nodi e $d$ dimensione del dominio più ampio. Tuttavia, il dominio in questo contesto rappresenta un insieme di tuple, la cui dimensione cresce esponenzialmente con il numero di variabili per nodo. La *tree width* della decomposizione, definita come la dimensione massima dei nodi meno uno, influenza la complessità che diventa $O(nd^{w+1})$. La ricerca della decomposizione a larghezza minima è anch'essa NP-hard, ma in pratica si adottano euristiche per ottenere decomposizioni sufficientemente compatte. poi si risolve con [[Struttura di un CSP - Struttura ad albero]]

Si osserva che se esiste un *cycle cutset* di dimensione $c$, allora la *tree width* è minore di $c + 1$, potenzialmente molto inferiore. Sebbene la decomposizione ad albero sia computazionalmente vantaggiosa, essa richiede memoria esponenziale rispetto alla *tree width*, mentre il *cutset conditioning* utilizza memoria lineare.

Infine, la simmetria nei valori delle variabili, detta *value symmetry*, può ampliare inutilmente lo spazio delle soluzioni. La permutazione dei valori che genera soluzioni equivalenti può essere eliminata attraverso vincoli di rottura della simmetria (*symmetry-breaking constraint*), imponendo un ordinamento arbitrario sui valori assegnati alle variabili, riducendo lo spazio di ricerca di un fattore $d!$. Sebbene sia in generale NP-hard eliminare tutte le simmetrie, la riduzione parziale dello spazio simmetrico si è dimostrata efficace in molteplici contesti applicativi.


