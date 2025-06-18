---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca alpha-beta pruning
---
L'algoritmo di **alfa–beta pruning** rappresenta un'**estensione fondamentale** della [[Ricerca MiniMax|ricerca Min-Max]] all'interno degli [[Giochi a somma zero|giochi a somma zero]], questo algoritmo ha la capacita di tagliare rami sicuramente infruttuosi. La **potatura**(**pruning**) consente di abbassare la [[Complessita|complessità]] del algoritmo.

si mantengono due parametri $\alpha$ e $\beta$ che rappresentano, rispettivamente, il valore **minimo garantito** al giocatore **MAX** e il valore **massimo garantito** al giocatore **MIN** lungo il cammino esplorato in profondità:
- $\alpha$ è il valore della migliore scelta trovata finora per MAX ("almeno").
- $\beta$ è il valore della migliore scelta trovata finora per MIN ("al massimo").
Durante l'esplorazione, se si scopre che il valore corrente di un **nodo foglia** è peggiore di una decisione già nota a un livello superiore (ovvero, se $v \leq \alpha$ per MIN o $v \geq \beta$ per MAX), allora si può interrompere la valutazione degli altri rami del nodo, poiché essi non influiranno sul risultato finale. quando potrà potare dipende dal al ordine in cui vengono esplorati i nodi dell’albero.
questa cosa si può estendere anche ai nodi intermedi permettendo cosi di tagliare interi sottoalberi anziché singoli nodi **foglia**.

Come il [[Ricerca MiniMax|minimax]] l algoritmi **alfa-beta pruning** è di tipi [[Ricerca in profondita (DF)|depth-first]] il che rende possibile mantenere in memoria un solo cammino attivo alla volta, permettendo un’efficiente gestione degli intervalli $[\alpha, \beta]$ lungo il percorso.
![[IMG - Esempio Comportamento ricerca alfa-beta pruning.png]]

lo pseudo codice di questo algoritmo:
```pseudo

\begin{algorithm}
\caption{Alpha-Beta Search}
\begin{algorithmic}
\Function{Alpha-Beta-Search}{game, state}
    \State player $\gets$ game.\Call{To-Move}{state}
    \State $(value, move) \gets$ \Call{Max-Value}{game, state, $-\infty$, $+\infty$}
    \Return move
\EndFunction

\State

\Function{Max-Value}{game, state, $\alpha$, $\beta$}
    \If{game.\Call{Is-Terminal}{state}}
        \Return (game.\Call{Utility}{state, player}, null)
    \EndIf
    \State $v \gets -\infty$
    \ForAll{$a \in$ game.\Call{Actions}{state}}
        \State $(v2, a2) \gets$ \Call{Min-Value}{game, game.\Call{Result}{state, a}, $\alpha$, $\beta$}
        \If{$v2 > v$}
            \State $v \gets v2$
            \State $move \gets a$
        \EndIf
        \State $\alpha \gets \max(\alpha, v)$
        \If{$v \geq \beta$}
            \Return $(v, move)$
        \EndIf
    \EndFor
    \Return $(v, move)$
\EndFunction

\State

\Function{Min-Value}{game, state, $\alpha$, $\beta$}
    \If{game.\Call{Is-Terminal}{state}}
        \Return (game.\Call{Utility}{state, player}, null)
    \EndIf
    \State $v \gets +\infty$
    \ForAll{$a \in$ game.\Call{Actions}{state}}
        \State $(v2, a2) \gets$ \Call{Max-Value}{game, game.\Call{Result}{state, a}, $\alpha$, $\beta$}
        \If{$v2 < v$}
            \State $v \gets v2$
            \State $move \gets a$
        \EndIf
        \State $\beta \gets \min(\beta, v)$
        \If{$v \leq \alpha$}
            \Return $(v, move)$
        \EndIf
    \EndFor
    \Return $(v, move)$
\EndFunction
\end{algorithmic}
\end{algorithm}
```
#### Move ordering
L’efficacia dell’**alpha–beta pruning** dipende in modo critico dall’**ordine in cui vengono esaminati i nodi** dell’**albero di gioco**. Se le mosse vengono esplorate in un ordine subottimale, la potatura sarà minima o nulla. è vantaggioso **esplorare prima i rami più promettenti**, in modo da poter fare un taglio.

In termini computazionali, un **ordinamento perfetto** permetterebbe di ridurre il numero di nodi esplorati da $O(b^m)$ del [[Ricerca MiniMax|minimax]] a $O(b^{m/2})$, con una conseguente riduzione del **fattore di diramazione effettivo** da $b$ a $\sqrt{b}$, mentre con un ordinamento casuale, invece, il numero medio di nodi esplorati cresce come $O(b^{3m/4})$, che è sensibilmente peggiore rispetto al caso ideale. 

l'**ordinamento perfetto** implicherebbe già conoscere la strategia ottimale e quindi non è utilizzabile ma fa da base di confronto, la si approssima con **euristiche di ordinamento**.  Cercando di analizare prima Le mosse promettenti in modo da trovare prima il limite, queste sono dette **killer moves**, e il tentativo sistematico di provarle per prime è noto come **killer move heuristic**.


Risultati ancora migliori si ottengono introducendo **strategie dinamiche** di ordinamento, come l’uso delle mosse che si sono dimostrate efficaci in precedenza. Questo approccio sfrutta la **coerenza locale** tra mosse promettenti, ipotizzando che una mossa efficace in una configurazione simile possa esserlo anche nella posizione corrente. In particolare, l’uso di tecniche di **[[Ricerca con approfondimento iterativo (IDS)]]** permette di raffinare progressivamente l’ordine delle mosse. Il procedimento consiste nel:
1. Esplorare l’albero di gioco a profondità 1, raccogliendo valutazioni euristiche.
2. Riutilizzare l’ordine risultante per la ricerca a profondità 2.
3. Ripetere il processo fino alla profondità massima consentita.
Il costo computazionale aggiuntivo di questa tecnica è compensato dal guadagno ottenuto grazie a un miglior ordinamento delle mosse. 
 
un altra situazione da considerare sono le **transpositions**, ovvero situazioni in cui stati identici possono essere raggiunti attraverso sequenze di mosse differenti. Questo comporta la possibilità di rientrare in uno stesso stato da cammini diversi, con un conseguente aumento esponenziale del costo computazionale se non opportunamente gestito. L’introduzione di una **transposition table**, che memorizza i valori euristici già calcolati per ciascuno stato visitato, consente di riutilizzare le valutazioni e di evitare esplorazioni ridondanti.


### Tipi di strategie (extra)
Anche con un ordinamento ottimizzato, tuttavia, l’algoritmo minimax con pruning risulta insufficiente per giochi con altissimo fattore di diramazione come il Go. Questo problema, già individuato da Shannon , ha portato alla distinzione tra due strategie di ricerca:
- La **strategia di Tipo A**, che esplora **in larghezza** fino a una certa profondità fissata, usando una funzione euristica per valutare i nodi terminali.
- La **strategia di Tipo B**, che persegue **linee promettenti in profondità**, evitando esplorazioni superficiali di rami meno rilevanti.

Storicamente, i programmi di scacchi hanno fatto uso principalmente della strategia di Tipo A, mentre per il Go e altri giochi ad alta complessità, l’approccio di Tipo B ha mostrato prestazioni superiori. Più recentemente, approcci ibridi di tipo B, supportati da tecniche come il **Monte Carlo Tree Search** e le **reti neurali**, hanno permesso prestazioni di livello campione del mondo anche in giochi tradizionalmente ostici per la ricerca minimax.


#### Euristiche 
La ricerca euristica con potatura Alpha–Beta rappresenta un’estensione fondamentale dell’algoritmo MINIMAX, adattata per affrontare i limiti computazionali insiti nei giochi complessi come gli scacchi. In tale contesto, l’algoritmo viene modificato per interrompere l’esplorazione dell’albero di gioco prima di raggiungere stati terminali, sostituendo la funzione $UTILITY$ con una funzione di valutazione euristica $EVAL$, la quale stima l’utilità di uno stato per un determinato giocatore. Parallelamente, il test terminale viene sostituito da un test di cutoff, indicato come $IS\text{-}CUTOFF(s, d)$, che può basarsi su una varietà di criteri, tra cui la profondità di ricerca $d$ e proprietà specifiche dello stato $s$.

La formulazione dell’algoritmo euristico H-MINIMAX è data da:

$$
H\text{-}MINIMAX(s, d) = 
\begin{cases}
EVAL(s, MAX) & \text{se } IS\text{-}CUTOFF(s, d) \\
\max\limits_{a \in Actions(s)} H\text{-}MINIMAX(RESULT(s, a), d + 1) & \text{se } TO\text{-}MOVE(s) = MAX \\
\min\limits_{a \in Actions(s)} H\text{-}MINIMAX(RESULT(s, a), d + 1) & \text{se } TO\text{-}MOVE(s) = MIN
\end{cases}
$$

La funzione $EVAL(s, p)$ restituisce una stima dell’utilità attesa dello stato $s$ per il giocatore $p$. Essa è vincolata a due requisiti essenziali: in primo luogo, deve restituire esattamente il valore della funzione $UTILITY$ per gli stati terminali; in secondo luogo, per stati non terminali, il valore stimato deve trovarsi all’interno dell’intervallo definito tra perdita e vittoria, ovvero $UTILITY(loss, p) \leq EVAL(s, p) \leq UTILITY(win, p)$. Inoltre, è cruciale che il calcolo di $EVAL$ sia computazionalmente efficiente, affinché il vantaggio della potatura risulti effettivo.

La nozione di “probabilità di vittoria” appare, a prima vista, contraddittoria nei giochi deterministici come gli scacchi, in cui l’incertezza non deriva da elementi casuali ma dalla limitazione delle risorse computazionali che impedisce una valutazione esaustiva dell’albero di gioco. Questa incertezza viene gestita stimando il valore medio atteso di una categoria di stati: ad esempio, se si considerano gli endgame con due pedoni contro uno, e si osserva che l’82% di tali stati conduce a vittoria, il 2% a sconfitta e il 16% a patta, la valutazione attesa sarà data da:

$$
(0.82 \times 1) + (0.02 \times 0) + (0.16 \times \frac{1}{2}) = 0.90
$$

Questa logica evidenzia come la funzione di valutazione sia costruita a partire da caratteristiche, o *feature*, dello stato. Ogni feature $f_i(s)$ corrisponde a un attributo significativo — ad esempio, il numero di alfieri bianchi — e viene ponderata da un peso $w_i$ che ne esprime l’importanza. L’intera funzione assume così la forma di una combinazione lineare pesata:

$$
EVAL(s) = \sum_{i=1}^n w_i f_i(s)
$$

Questa struttura è nota come funzione lineare pesata (*weighted linear function*) e consente di approssimare il valore di uno stato sommando contributi numerici indipendenti. Nei giochi come gli scacchi, questa pratica è radicata nella tradizione, con valori standard assegnati ai pezzi: pedone = 1, cavallo o alfiere = 3, torre = 5, regina = 9. Altri aspetti strategici, come la sicurezza del re o la struttura pedonale, possono essere quantificati in frazioni di pedone.

Tuttavia, tale modello implica un’importante assunzione di indipendenza tra le feature. In
