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
L'algoritmo di **alfa–beta pruning** rappresenta un'**estensione** della [[Ricerca MiniMax|ricerca Min-Max]] all'interno degli [[Giochi a somma zero|giochi a somma zero]], questo algoritmo ha la capacita di tagliare rami sicuramente infruttuosi. La **potatura**(**pruning**) consente di abbassare la [[Complessita|complessità]] del algoritmo.

si mantengono due parametri $\alpha$ e $\beta$ che rappresentano, rispettivamente, il valore **minimo garantito** al giocatore **MAX** e il valore **massimo garantito** al giocatore **MIN** lungo il cammino esplorato in profondità:
- $\alpha$ è il valore della migliore scelta trovata finora per MAX ("almeno").
- $\beta$ è il valore della migliore scelta trovata finora per MIN ("al massimo").
Durante l'esplorazione, se si scopre che il valore corrente di un **nodo foglia** è peggiore di una decisione già nota a un livello superiore (ovvero, se $v \leq \alpha$ per MIN o $v \geq \beta$ per MAX), allora si può interrompere la valutazione degli altri rami del nodo, poiché essi non influiranno sul risultato finale. quando potrà potare dipende dall ordine in cui vengono esplorati i nodi dell’albero.
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
			\State $v,move \gets v2, a$
	        \State $\alpha \gets \max(\alpha, v)$
        \EndIf
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
            \State $v ,move \gets v2,a$
	        \State $\beta \gets \min(\beta, v)$
        \EndIf
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

#### Euristiche 
un modo per abbassare la [[Complessita|complessità computazione]] del algoritmo **alpha-beta pruning** è utilizzare delle **euristiche**, in particolare l’algoritmo non si spinge fino agli stati terminali dell’albero di gioco, ma interrompe anticipatamente la ricerca attraverso un test di cutoff $IS\text{-}CUTOFF(s, d)$, il quale può essere basato sulla profondità raggiunta $d$ oppure su proprietà strutturali dello stato $s$. 

Al posto della funzione $UTILITY$ calcolata solo sugli stati finali, viene utilizzata una funzione di valutazione euristica $EVAL(s, p)$ che stima il valore atteso del **utilita** dello stato $s$ per il giocatore $p$.
deve rispettare 2 condizioni: 
- il calcolo di $EVAL$ deve risultare computazionalmente efficiente perche l obiettivo è velocizzare una ricerca
- Deve restituire esattamente $UTILITY(s, p)$ per ogni stato **terminale** mentre per gli stati interni deve valere$UTILITY(loss, p) \leq EVAL(s, p) \leq UTILITY(win, p)$. 

se definisce il valore valore $$
H\text{-}MINIMAX(s, d) = 
\begin{cases}
EVAL(s, MAX) & \text{se } IS\text{-}CUTOFF(s, d) \\
\max\limits_{a \in Actions(s)} H\text{-}MINIMAX(RESULT(s, a), d + 1) & \text{se } TO\text{-}MOVE(s) = MAX \\
\min\limits_{a \in Actions(s)} H\text{-}MINIMAX(RESULT(s, a), d + 1) & \text{se } TO\text{-}MOVE(s) = MIN
\end{cases}
$$
che sostituisce quello di $MINIMAX$
 

Nel caso di giochi **[[Definizione di problemi-Ambienti|deterministici a informazione perfetta (completamente osservabili)]]**, l’incertezza non deriva da **elementi casuali**, bensì dalla limitazione delle risorse computazionali che impedisce di valutare completamente l’albero delle possibilità. 
Di conseguenza, la valutazione dello stato assume il significato di valore medio stimato su una classe di stati simili.  

La funzione $EVAL$ puo essere costruita in vario modo, spesso questo dipende dal esperienza o da parametri e criteri specifici del gioco in cui è l agente, puo essere **ad esempio** [[Combinazioni Lineari|combinazione lineare pesata]] di caratteristiche rilevanti dello stato, chiamate ***feature***. Ogni feature $f_i(s)$ rappresenta un attributo significativo, come il numero di pezzi o la struttura pedonale nel caso degli scacchi, mentre il peso $w_i$ ne esprime l’importanza strategica. La funzione assume pertanto la forma:$$
EVAL(s) = \sum_{i=1}^n w_i f_i(s)
$$questo tipo di approccio funziona bene se le feature sono indipendenti ma spesso questo non è il caso.  un altro caso in cui non funziona bene e se le singole feature cambiano di importanza man mano che il gioco evolve. Per queste tipi di situazioni si utilizano pesi non lineari.


la funzione $EVAL(s)$ viene usata per fare valutare i nodi piu profondi che superano il test di **cutoff**. il test **cutoff** 	è una funzione $IS-CUTOFF(s,d)$ che da $true$ se supera la profondità $d$ e false altrimenti, questo permette di scegliere un $d$ fisso compatibile con il tempo di computazoine disponibile. 

un altor modo per implementare l algoritmo consiste nell’utilizzare la ricerca a [[Ricerca con approfondimento iterativo (IDS)|profondita iterativo]] incrementano $d$. Al termine di ciascuna iterazione, viene conservata la miglior mossa trovata, e se il tempo scade, si restituisce il risultato più profondo completato. Questa strategia consente anche un uso efficiente delle **tabelle di trasposizione**, e risultati di iterazioni precedenti possono essere usati per fare una miglioro **move ordering**.


il **cutoff** ha due problematiche principali:
- è prono a dare buone mosse ma che non sono stabili quindi bastano poche mosse per ribaltare la valutazione. Per evitare errori di questo tipo, la funzione $EVAL$ dovrebbe essere applicata solo a posizioni *quiescenti*, ovvero situazioni stabili prive di minacce tattiche immediate. In presenza di posizioni non quiescenti, la condizione $IS\text{-}CUTOFF(s, d)$ restituisce falso, forzando un’estensione della ricerca. *quiescence search*
- **effetto orizzonte** (***horizon effect***): in cui un ribaltamento del valore di valutazione viene **apparentemente** evitata perché spinta oltre il limite di profondità $d$ considerato, applicando mosse che ritardano la cosa ma non la evitano. per affrontare questo problema ***singular extensions***, che estende selettivamente la ricerca oltre il **cutoff** solo per quelle mosse che risultano nettamente superiori alle alternative.

### Tipi di strategie (extra)
Anche con un ordinamento ottimizzato, tuttavia, l’algoritmo minimax con pruning risulta insufficiente per giochi con altissimo fattore di diramazione come il Go. Questo problema, già individuato da Shannon , ha portato alla distinzione tra due strategie di ricerca:
- La **strategia di Tipo A**, che esplora **in larghezza** fino a una certa profondità fissata, usando una funzione euristica per valutare i nodi terminali.
- La **strategia di Tipo B**, che persegue **linee promettenti in profondità**, evitando esplorazioni superficiali di rami meno rilevanti.
Storicamente, i programmi di scacchi hanno fatto uso principalmente della strategia di Tipo A, mentre per il Go e altri giochi, l’approccio di Tipo B ha mostrato prestazioni superiori. Più recentemente, approcci ibridi di tipo B, supportati da tecniche come il **[[Ricerca albero Monte Carlo (MCST)|Monte Carlo Tree Search]]** e le **[[Reti Neurali (NN)|reti neurali]]**, hanno permesso prestazioni di livello campione del mondo anche in giochi tradizionalmente ostici per la ricerca minimax.