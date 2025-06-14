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
Il **problema della Soddisfacibilità** (**SAT**) è un problema nel ambito della [[Logica|logica]]. 
dato un enunciato $\alpha$ si occupa di decidere se esiste almeno un **modello** $m$ che **soddisfa** $\alpha$

Per la sua trattazione formale, la formula viene generalmente espressa in [[Forma normale congiuntiva (CNF)|Forma normale congiuntiva (CNF)]]

Il problema SAT è il primo problema che è stato dimostrato essere [[Classi di complessita - NP-Completo|NP-completo]], come mostrato dal teorema di Cook-Levin. 





Una forma particolarmente studiata è il 3-SAT, in cui ogni clausola contiene esattamente tre letterali. Un esempio rappresentativo è:

$$
\phi = (x_1 \lor \neg x_2 \lor x_3) \land (\neg x_1 \lor x_4 \lor \neg x_5) \land (x_2 \lor x_3 \lor \neg x_4)
$$

Questa restrizione mantiene la [[Classi di complessita - NP-Completo|NP-completezza]] del problema, ma lo rende particolarmente utile per costruire riduzioni verso altri problemi. All’interno della [[Macchina di turing k-nastri]], il SAT rappresenta una delle principali istanze per analizzare l'efficienza computazionale in scenari non deterministici.

I metodi di risoluzione possono essere divisi in esatti e approssimati. Tra i primi, il backtracking con pruning e i SAT solver basati su Conflict-Driven Clause Learning (CDCL) sono i più efficaci in ambito pratico. Tra gli approcci euristici si trovano algoritmi ispirati alla natura, come quelli genetici e il simulated annealing. SAT trova applicazione in ambiti quali la verifica di circuiti digitali, l'intelligenza artificiale, la [[Logica del primo ordine (FOL)]] e la sicurezza informatica.

Esistono inoltre varianti come MAX-SAT, dove si mira a massimizzare il numero di clausole soddisfatte, oppure l’UNSAT-core extraction, utile per identificare sottostrutture contraddittorie. Tali estensioni collegano il problema SAT ad altri aspetti della [[Complessita|teoria della complessità]], inclusi i problemi di ottimizzazione e di inferenza logica.

La rappresentazione grafica della struttura delle clausole e delle dipendenze tra letterali, attraverso grafi di implicazione e diagrammi di ricerca, consente di visualizzare l’evoluzione dell’algoritmo di risoluzione e i conflitti emergenti durante l’assegnazione delle verità.
