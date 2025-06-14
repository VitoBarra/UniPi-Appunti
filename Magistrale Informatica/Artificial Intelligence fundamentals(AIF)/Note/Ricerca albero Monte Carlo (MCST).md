---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca albero Monte Carlo (MCTS)
---
la **ricerca Monte Carlo** o **Monte Carlo Tree Search** (MCTS) è un [[Problemi di ricerca|algoritmo di ricerca]] per [[Ricerca in ambienti competitivi|ambienti competitivo]] [[Giochi a somma zero|zero-sum]] è un tipo di ricerca che funziona bene per giochi con **branch factor** $b$ troppo grade, dove ad esempio l [[Ricerca alpha-beta pruning|alpha-beta pruning]] fallirebbe infattibilità computazionale.


La strategia **MCTS** stima il valore di uno stato come media dell'utilità calcolata su più simulazioni complete a partire da quello stato. Ogni simulazione è detta ***playout*** o ***rollout***. alterna mosse per entrambi i giocatori fino al raggiungimento di una posizione terminale, dove il risultato è determinato dalle **regole stesse del gioco**. Se le uniche uscite possibili sono vittoria o sconfitta, la media delle utilità corrisponde alla percentuale di vittorie.

Se le mosse durante il **playout** sono selezionate casualmente, il risultato rifletterà il miglior esito in caso di gioco casuale. Per ottenere informazioni significative, è necessario adottare una ***playout policy*** che indirizzi la simulazione verso mosse promettenti. Tali politiche sono spesso apprese tramite ***self-play*** mediante reti neurali, oppure arricchite da euristiche specifiche al gioco 

La forma più semplice è la ***pure Monte Carlo search***, che esegue $N$ simulazioni dalla posizione corrente e tiene traccia di quale mossa ha la percentuale migliore di vittoria, questo approccio funziona bene per giochi stocastici, ma non la maggior parte dei giochi.
generalmente è necessario una ***selection policy*** che sceglie quale nodi provare, questa  bilancia due aspetti:
- l'***esplorazione*** scelta di stati poco visitati 
- l'***esploitazione*** scelta di quelli con buoni risultati in iterazione passate per ottenere una migliore stima della percentuale di vittoria 


La MCTS costruisce progressivamente un albero di ricerca attraverso quattro fasi iterative:
- **Selection**: Si parte dalla radice e si selezionano successivamente i nodi figli seguendo la **selection policy**.
- **Expansion**: Si espande l’albero generando un nuovo figlio del nodo selezionato. Alcune varianti ne generano più di uno.
- **Simulation**: Si esegue un playout dalla nuova posizione, selezionando mosse per entrambi i giocatori secondo la **playout policy**. Le mosse non sono registrate nell’albero.
- **Back-propagation**: Il risultato del playout viene propagato verso l’alto nell’albero, aggiornando le statistiche di ciascun nodo fino alla radice. 
Il processo è ripetuto per un numero prefissato di iterazioni o fino al termine del tempo disponibile, e infine si sceglie la mossa con il maggior numero di playout. 
Nonostante si possa pensare di preferire la mossa con la media di utilità più alta, il numero di playout è un indicatore più affidabile della robustezza statistica della valutazione, privilegiando mosse con valutazioni più stabili.

![[IMG - Ricerca albero Monte Carlo.png]]


l algoritmo in pseudo codice che ritorna un azione:
```pseudo
\begin{algorithm}
\caption{Monte Carlo Tree Search}
\begin{algorithmic}
\Function{MONTE-CARLO-TREE-SEARCH}{state}
    \State tree $\gets$ \Call{Node}{state}
    \While{IS-TIME-REMAINING()}
        \State leaf   $\gets$ \Call{Select}{tree}
        \State child  $\gets$ \Call{Expand}{leaf}
        \State result $\gets$ \Call{Simulate}{child}
        \State \Call{Back-Propagate}{result, child}
    \EndWhile
    \Return the move in \Call{Actions}{state} whose node has highest number of playouts
\EndFunction
\end{algorithmic}
\end{algorithm}

```
Una **selection policy** efficace è l ***Upper Confidence bounds applied to Trees*** (UCT), basato sulla formula **UCB1**:
**sia**
- $U(n)$ è l’utilità totale dei playout che attraversano il nodo $n$
- $N(n)$ è il numero di playout in quel nodo
- $C$ è una costante che regola il compromesso tra esplorazione ed esploitazione
**allora** la formula la formula **UCB1**:$$
\text{UCB1}(n) = \frac{U(n)}{N(n)} + C \cdot \sqrt{\frac{\log N(\text{PARENT}(n))}{N(n)}}
$$ dove 
- Il termine $\cfrac{U(n)}{N(n)}$ rappresenta **l’esploitazione** (media dell’utilità)
-  $\sqrt{\frac{\log N(\text{PARENT}(n))}{N(n)}}$ guida l’esplorazione: è alto quando $N(n)$ è basso, incentivando la visita a nodi ancora poco esplorati. 
un valore tipico per $C$  è $\cfrac{1}{\sqrt{2}}$ se  $\cfrac{U(n)}{N(n)} \in [0,1]$ ma spesso viene scelto empiricamente.

Il tempo necessario per un singolo playout cresce linearmente con la profondità dell’albero, a differenza della crescita esponenziale tipica della ricerca [[Ricerca alpha-beta pruning|alfa–beta]]. 

L’[[Ricerca alpha-beta pruning|alfa–beta]] ricerca il cammino verso il nodo con la massima valutazione, supponendo che l’avversario minimizzi tale valore; un errore singolo nella funzione di valutazione può indirizzare la scelta verso un cammino errato.
La MCTS, affidandosi all'aggregazione di molte simulazioni, è più resistente a errori isolati. 

È possibile combinare MCTS con **funzioni di valutazione**, interrompendo anticipatamente i playout e applicando una valutazione euristica, oppure dichiarando un pareggio (*early playout termination*). 

La natura stocastica della MCTS la rende meno adatta a situazioni dove una singola mossa può cambiare radicalmente l’esito della partita, o dove stati chiaramente vincenti richiedono molte mosse per essere confermati nei playout.