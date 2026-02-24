---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con bayesian network
---
L'**inferenza nelle [[Bayesian network|reti Bayesiane]]** seguene le stesse linee del [[Inferenza con Full Joint distribution|inferenza sulla full joint distributuion]]  dove la [[Bayesian network|rete Bayesiana]] fornisce una rappresentazione compatta della [[Full Joint Distribution (FJD)|distribuzione congiunta]] 



### Complessita
La [[Complessita|complessità]] dell’**inferenza esatta** nelle **[[Bayesian network|reti bayesiane]]** dipende in modo determinante dalla loro struttura topologica. Le reti appartenenti alla classe dei polialberi, nelle quali esiste al più un solo cammino non diretto tra due nodi, presentano proprietà particolarmente favorevoli. In tali strutture, il tempo e lo spazio necessari per l’inferenza esatta crescono linearmente con la dimensione della rete, definita dal numero di voci nelle tabelle di probabilità condizionate (CPT). Quando il numero di genitori per ciascun nodo è limitato da una costante, la complessità risulta quindi lineare anche rispetto al numero totale di nodi. Questo comportamento si mantiene per qualsiasi ordinamento coerente con la topologia del grafo.

Nelle reti connessi multipli, la situazione cambia radicalmente. In tali casi, l’eliminazione delle variabili può richiedere tempo e spazio esponenziali nel caso peggiore, anche quando ogni nodo possiede un numero limitato di genitori. Tale risultato deriva dal fatto che l’inferenza nelle reti bayesiane include, come caso particolare, l’inferenza nella logica proposizionale, la quale è un problema NP-difficile. La dimostrazione si ottiene mediante una riduzione dal problema di soddisfacibilità proposizionale, costruendo una rete bayesiana che rappresenti un’istanza di 3-SAT. Le variabili proposizionali diventano nodi radice con probabilità a priori $0.5$, mentre i nodi corrispondenti alle clausole sono deterministici e dipendono dai rispettivi letterali. Un ulteriore nodo rappresenta la congiunzione di tutte le clausole. Calcolando $P(S = true)$, si ottiene che la formula logica è soddisfacibile se e solo se $P(S = true) > 0$, mentre $P(S = true) = 0$ indica insoddisfacibilità. Da ciò segue che l’inferenza nelle reti bayesiane è NP-difficile.

La relazione può essere estesa ulteriormente. Poiché la probabilità associata a ciascuna assegnazione soddisfacente è $2^{-n}$, con $n$ variabili proposizionali, il numero di assegnazioni soddisfacenti risulta $P(S = true)/(2^{-n})$. Calcolare tale quantità equivale a risolvere un problema #P-completo, da cui discende che l’inferenza in reti bayesiane è #P-difficile, una classe di complessità ancora più ampia rispetto ai problemi NP.

Esiste inoltre una stretta connessione tra la complessità dell’inferenza bayesiana e quella dei problemi di soddisfacimento di vincoli discreti. La difficoltà di risoluzione dipende dalla “somiglianza ad un albero” del grafo dei vincoli, misurata da parametri come l’ampiezza d’albero (tree width), applicabile direttamente anche alle reti bayesiane. L’algoritmo di eliminazione delle variabili può infatti essere generalizzato per operare sia su problemi CSP sia su reti bayesiane.

L’inferenza può essere anche ridotta al problema della soddisfacibilità, consentendo di sfruttare i metodi sviluppati per il SAT solving. In particolare, l’equivalente formulazione come conteggio pesato dei modelli (weighted model counting, WMC) permette di calcolare la somma dei pesi delle assegnazioni soddisfacenti, dove ogni peso corrisponde al prodotto delle probabilità condizionate delle variabili dato il valore dei loro genitori. L’ottimizzazione raggiunta dagli algoritmi di SAT solving rende l’approccio WMC competitivo e, in reti con ampia ampiezza d’albero, talvolta superiore agli algoritmi esatti tradizionali.
