---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

# Planning - Euristiche indipendenti dal dominio
---
Nel [[Planning]],  si possono usare **funzioni euristiche** $h(\cdot)$ per migliorare l’efficienza della ricerca, sia essa [[Planning - Ricerca Forward|Ricerca Forward]] o [[Planning - Ricerca Backward|Ricerca Backward]]. La rappresentazione **[[Rappresentazione del ambiente|fattorizzata]]** degli stati e delle azioni consente di costruire euristiche **indipendenti dal dominio**, superando i limiti delle rappresentazioni **[[Rappresentazione del ambiente|atomiche]]**, dove l’analisi interna dello stato non è possibile.

Un modo generale per derivare euristiche consiste nel **rilassamento del problema**, cioè nella costruzione di una versione semplificata del problema originale, la cui soluzione fornisce un limite inferiore al costo reale. Esistono due principali categorie di rilassamento:  
- l’**aggiunta di archi al grafo degli stati**, che rende più semplice la connessione fra stato iniziale e obiettivo;  
 - la **riduzione del numero di stati** attraverso una rappresentazione astratta.  

Tra le euristiche più note ottenute tramite rilassamento vi sono:
- **Ignore-preconditions heuristic**: elimina tutte le **precondizioni delle azioni**, rendendole universalmente applicabili. Ogni fluent nello stato **goal** diventa potenzialmente raggiungibile in $1$ passo altrimenti l obiettivo è impossibile da raggiungere. Si potrebbe contare il numero di fluent del goal non soddisfatti e usare quello come euristica ma   alcune azioni possono soddisfare più goal contemporaneamente e altre possono annullare i **fluent** gia generati, quindi non sarebbe un euristica accurata. invece si vuole usare il **numero minimo di azioni** la cui **unione di effetti** copre tutti i **goal non ancora soddisfatti**. Questo problema è formalmente equivalente a un’istanza del problema di ***set-cover*** che è di [[Complessita|classe NP-hard]]. In pratica, si utilizza un **algoritmo greedy** che, a ogni passo, seleziona l’azione che copre il maggior numero di goal ancora insoddisfatti. Questa approssimazione produce una stima del costo entro un fattore $\log n$ dal valore ottimale, dove $n$ è il numero dei goal fluent. Tuttavia, l’approssimazione comporta la perdita della [[Ricerca informata - Proprieta delle euristiche|ammissibilità]], poiché il valore stimato può superare il costo effettivo.
- **Ignore-delete-lists heuristic**: consiste nel rimuovere dagli effetti di tutte le azioni le **literals negative**, cioè tutto ciò che potrebbe invalidare altri goal già raggiunti, cosi facendo ogni azione puo solo aggiungere **fluent goal** è il cambiamento diventa monotono. Questo rilassamento trasforma il problema originale in uno in cui **il progresso verso il goal è sempre possibile** siccome il grafo degli stati non ha piu minimi locali e non c è la necessità di fare backtracking. La soluzione esatta al problema rilassato rimane [[Complessita|NP-hard]] ma si puo usare la [[Ricerca Hill Climbing|Ricerca Hill Climbing]] per una soluzione approssimativa in tempo polinomiale.

### Pruning indipendenti dal dominio
La rappresentazione fattorizzata consente inoltre **tecniche di pruning indipendenti dal dominio**. 
- Il **symmetry reduction** elimina stati equivalenti o simmetrici, riducendo la ramificazione della ricerca.
- Il **forward pruning**, invece, limita l’esplorazione alle azioni più promettenti, definite ***preferred actions***, che appartengono a un piano nel **problema rilassato**. Queste strategie mirano a concentrare la ricerca nelle regioni più rilevanti dello spazio, riducendo i costi computazionali anche a scapito dell’**ottimalità**.

avvolte, la pianificazione è semplificata dalla presenza di **sottogoal serializzabili**, in cui gli obiettivi possono essere raggiunti in una sequenza ordinata senza che le azioni successive interferiscano con quelle precedenti. Questa proprietà riduce drasticamente la complessità, consentendo pianificazioni lineari prive di backtracking.

### Astrazione degli stati
Un approccio per costruire **euristiche** consiste nella definizione di **stati astratti**, che realizzano una mappatura **molti-a-uno** tra gli **stati concreti** del problema e una versione semplificata dello spazio di ricerca. Per costruire i **stati astratti** si possono ignorare alcuni **fluents**, riducendo così la dimensione complessiva dello spazio degli stati.

La soluzione del problema astratto fornisce una **stima euristica** del costo necessario per raggiungere l’obiettivo nello spazio originale. Poiché le azioni nello spazio astratto non aumentano il costo rispetto a quello reale, l’euristica risultante è [[Ricerca informata - Proprieta delle euristiche|ammissibile]], rappresentando sempre un limite inferiore del costo effettivo.


Un ulteriore metodo consiste nella **decomposizione dei goal**, basata sull’assunzione di indipendenza tra sottogoal. Se l’obiettivo complessivo $G$ è suddiviso in insiemi disgiunti $G_1, \dots, G_n$, con relativi piani ottimali $P_1, \dots, P_n$, si possono stimare i costi con due formule:$$
h(G) = \max_i COST(P_i)
$$che mantiene l’ammissibilità, oppure$$
h(G) = \sum_i COST(P_i)
$$che fornisce una stima più precisa ma non necessariamente ammissibile. La scelta fra i due criteri dipende dal grado di indipendenza tra i sottogoal.