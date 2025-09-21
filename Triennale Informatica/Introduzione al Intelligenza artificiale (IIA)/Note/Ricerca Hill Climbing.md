---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Ricerca Hill Climbing
---
L'**algoritmo di ricerca Hill Climbing** appartiene alla categoria della [[Ricerca locale|ricerca locale]] e segue un approccio di tipo _[[Algoritmi greedy|greedy]]_. In ogni iterazione valuta gli stati adiacenti e, se esiste uno stato con una **valutazione migliore** rispetto all’attuale, l algoritmo lo sceglie come prossimo stato. In assenza di uno stato adiacente migliore, l'algoritmo termina, restituendo lo stato corrente come soluzione.

lo pseudo codice di questo è il seguente:
```pseudo
\begin{algorithm}
\caption{Hill-Climbing}
\begin{algorithmic}
\Function{HILL-CLIMBING}{problem}
    \State $current \gets problem.INITIAL$
    \While{true}
        \State $neighbor \gets$ uno stato successore di $current$ con valore più alto
        \If{\Call{VALUE}{neighbor} $\leq$ \Call{VALUE}{current}}
            \Return $current$
        \EndIf
        \State $current \gets neighbor$
    \EndWhile
\EndFunction
\end{algorithmic}
\end{algorithm}
```
Durante l’esecuzione, l’algoritmo può incontrare difficoltà dovute alla presenza di massimi locali, creste o altopiani nella superficie dello spazio degli stati.


Per affrontare tali problematiche, sono state sviluppate diverse varianti migliorative dell'Hill Climbing:
1. È possibile consentire un numero limitato di mosse laterali durante la ricerca sugli altopiani. In presenza di uno stato adiacente con valutazione identica a quella corrente, l'algoritmo può comunque decidere di spostarsi in tale stato, nella speranza che l’altopiano sia in realtà uno **shoulder** che permetta ulteriori progressi. Per evitare cicli infiniti su massimi locali piatti, si impone un limite al numero di mosse laterali consecutive consentite.
2. Lo **_Hill-Climbing stocastico_** introduce una componente casuale nella scelta delle mosse ascendenti. Quando esistono più mosse migliorative, l’algoritmo seleziona una mossa a caso tra queste, con una [[Definizione di Probabilita|probabilità]] che può variare in funzione della pendenza. Sebbene la convergenza sia in genere più lenta.
3. Lo **_Hill-Climbing con prima scelta_** rappresenta un’applicazione pratica dello stocastico in spazi di ricerca molto ampi. Invece di generare e valutare tutti i successori, l’algoritmo produce successori uno alla volta in modo casuale, e si sposta immediatamente al primo stato che risulta migliorativo. Questa strategia si rivela particolarmente efficiente quando il numero di successori è elevato, riducendo il costo computazionale della valutazione.
4. Lo **_Hill-Climbing con riavvio casuale_** (_random restart_) adotta un approccio iterativo: esegue ripetutamente ricerche Hill Climbing da stati iniziali scelti casualmente, fino al raggiungimento di una soluzione. Poiché ogni avvio ha probabilità di successo $p$, il numero atteso di riavvii necessari per trovare la soluzione è $\cfrac{1}{p}$

L’efficacia dell’Hill Climbing dipende fortemente dalla morfologia dello spazio degli stati. In problemi con pochi massimi locali e altopiani, il metodo con riavvio casuale trova rapidamente soluzioni soddisfacenti. Tuttavia, in spazi più complessi, caratterizzati da un’elevata densità di massimi locali come nei problemi [[Classi di Complessita|NP-hard]], il rischio di bloccarsi su ottimi locali aumenta sensibilmente, benché una soluzione ragionevole possa comunque essere raggiunta dopo un numero limitato di riavvii.

