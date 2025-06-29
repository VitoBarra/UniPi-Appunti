---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Problemi della Sodisfacibilita (SAT)
---
Il **problema della Soddisfacibilità Booleana** (SAT) costituisce un nodo fondamentale nella [[Logica proposizionale]], con profonde implicazioni anche nell'ambito della [[Complessita]]. Esso consiste nel determinare se esiste un'assegnazione di valori di verità alle variabili proposizionali di una formula booleana tale che l'intera formula risulti vera. Per la sua trattazione formale, la formula viene generalmente espressa in [[Forma normale congiuntiva (CNF)]], una congiunzione di clausole, ognuna delle quali è una disgiunzione di letterali.

Formalmente, una formula in CNF assume la struttura:

$$
\phi = C_1 \land C_2 \land \dots \land C_m
$$

dove ciascuna clausola $C_i$ è del tipo:

$$
C_i = l_{i1} \lor l_{i2} \lor \dots \lor l_{ik}
$$

con $l_{ij}$ letterale, ovvero una variabile booleana o la sua negazione. Le [[Logica proposizionale]] fondamentali, come la congiunzione ($\land$), la disgiunzione ($\lor$) e la negazione ($\neg$), regolano il comportamento delle clausole all'interno del [[Logica proposizionale]].


Il problema SAT è il primo problema che è stato dimostrato essere [[Classi di complessita - NP-Completo]], come mostrato dal teorema di Cook-Levin. Questo risultato è stato fondamentale per la definizione delle [[Classi di Complessita]], fornendo un paradigma per la riduzione polynomial-time e per l'analisi della difficoltà intrinseca di numerosi altri problemi computazionali.
Una forma particolarmente studiata è il 3-SAT, in cui ogni clausola contiene esattamente tre letterali. Un esempio rappresentativo è:

$$
\phi = (x_1 \lor \neg x_2 \lor x_3) \land (\neg x_1 \lor x_4 \lor \neg x_5) \land (x_2 \lor x_3 \lor \neg x_4)
$$

Questa restrizione mantiene la [[Classi di complessita - NP-Completo|NP-completezza]] del problema, ma lo rende particolarmente utile per costruire riduzioni verso altri problemi. All’interno della [[Macchina di turing k-nastri]], il SAT rappresenta una delle principali istanze per analizzare l'efficienza computazionale in scenari non deterministici.

I metodi di risoluzione possono essere divisi in esatti e approssimati. Tra i primi, il backtracking con pruning e i SAT solver basati su Conflict-Driven Clause Learning (CDCL) sono i più efficaci in ambito pratico. Tra gli approcci euristici si trovano algoritmi ispirati alla natura, come quelli genetici e il simulated annealing. SAT trova applicazione in ambiti quali la verifica di circuiti digitali, l'intelligenza artificiale, la [[Logica del primo ordine (FOL)]] e la sicurezza informatica.

Esistono inoltre varianti come MAX-SAT, dove si mira a massimizzare il numero di clausole soddisfatte, oppure l’UNSAT-core extraction, utile per identificare sottostrutture contraddittorie. Tali estensioni collegano il problema SAT ad altri aspetti della [[Complessita|teoria della complessità]], inclusi i problemi di ottimizzazione e di inferenza logica.

La rappresentazione grafica della struttura delle clausole e delle dipendenze tra letterali, attraverso grafi di implicazione e diagrammi di ricerca, consente di visualizzare l’evoluzione dell’algoritmo di risoluzione e i conflitti emergenti durante l’assegnazione delle verità.
