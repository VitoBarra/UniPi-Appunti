---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - Threshold Boolean Networks
---
**Threshold Boolean Networks** sono una variante delle [[GRN - Boolean Networks|Boolean Networks]] progettata per semplificare la definizione delle funzioni di aggiornamento dei geni sostituendo le formule logiche con una combinazione di **pesi e soglie**. Questa formulazione mantiene la rappresentazione booleana degli stati dei geni ma rende il modello più semplice da costruire quando la logica precisa delle interazioni non è nota. 

Nelle reti regolatorie geniche i nodi rappresentano **geni** e gli archi rappresentano **influenze regolatorie** tra geni. In una threshold network ogni interazione $i\to j$ è associata a un **peso** $w_{ij}$ che indica il tipo di regolazione:
- $w_{ij}>0$ attivazione
- $w_{ij}<0$ inibizione
- $w_{ij}=0$ nessuna interazione
Ogni gene $i$ possiede inoltre una **soglia** $\theta_i$ che determina quando il gene si attiva. Lo stato del gene al tempo successivo dipende dalla **somma pesata** dei contributi dei geni regolatori.

Regola di aggiornamento:$$
x_i(t+1)=
\begin{cases}
1 & \text{se } \sum_j w_{ji}x_j(t) > \theta_i \\
0 & \text{altrimenti}
\end{cases}
$$La soglia è spesso scelta come $w_{i,j},\theta_i \in \mathbb{R}$ al caso semplici si utilizza valori discreti $+1$ (activation) o $-1$ (inhibition) e $\theta_i=0$. In questa configurazione il gene diventa attivo quando l'effetto complessivo degli **attivatori supera quello degli inibitori**. 

Una variante della regola considera anche lo **stato corrente del gene** tramite un peso $w_{ii}$ (self-interaction). In particolare, quando la somma pesata è esattamente uguale alla soglia ($\sum_j w_{j\not=i}x_j(t) = \theta_i$) si distingue tra due tipi di geni:
- **self-activating genes**: rimane attivo
- **non self-activating genes**: diventa inattivo
la regola estesa risulta quindi:$$
x_i(t+1)=
\begin{cases}
1 & \text{se } \sum_{j\ne i} w_{ij}x_j(t)>\theta_i \\
0 & \text{se } \sum_{j\ne i} w_{ij}x_j(t)<\theta_i \\
1 & \text{se } x_i\in M_{sa} \land \sum_{j\ne i} w_{ij}x_j(t)=\theta_i \\
0 & \text{se } x_i\notin M_{sa} \land \sum_{j\ne i} w_{ij}x_j(t)=\theta_i
\end{cases}
$$con $M_{sa}$ il set di geni **self-activating**

Le threshold networks possono essere viste anche come una forma estremamente semplice di **[[Rete di Percettroni|rete neurale artificiale]]**, poiché:
- ogni gene corrisponde a un neurone
- i pesi $w_{ij}$ corrispondono alle **forze sinaptiche**
- la funzione a soglia è equivalente a una **funzione di attivazione di Heaviside**
Nonostante questa analogia, nelle GRN i pesi non vengono **appresi tramite training**, ma sono fissati sulla base della conoscenza biologica delle interazioni regolatorie.$$
x_i(t+1) = H\!\left(\sum_j w_{ij} x_j(t) - \theta_i\right) 
\qquad
H(z) =
\begin{cases}
1 & z > 0 \\
0 & z \le 0
\end{cases}
$$


Le **Threshold Boolean Networks** rappresentano un ponte tra modellazione **qualitativa** e **quantitativa** delle [[GRN - Boolean Networks|Gene Regulatory Networks]]. Ogni gene agisce come un **integratore di segnali**, combinando l’influenza di più geni regolatori tramite una somma pesata confrontata con una soglia. La presenza della soglia introduce una minima **non linearità**, sufficiente a riprodurre dinamiche biologiche rilevanti come:
- **oscillazioni** (attrattori ciclici)
- **bistabilità** (più attrattori raggiungibili da diverse regioni dello spazio degli stati)

Dal punto di vista dinamico le threshold Boolean networks restano un caso particolare di [[GRN - Boolean Networks|Boolean Networks]]:
- lo stato della rete è un **vettore booleano**
- l’evoluzione dipende dalla strategia di aggiornamento (**sincrona** o **asincrona**)
- il sistema converge verso **attrattori** (stati stabili o cicli)

Spesso si utilizzano **aggiornamenti sincroni deterministici**, che producono dinamiche complesse ma interpretabili.

Dal punto di vista espressivo queste reti **non sono più potenti delle Boolean networks classiche**. Qualsiasi threshold Boolean network può essere codificata come una rete booleana standard introducendo variabili booleane aggiuntive e regole logiche che simulano la **somma pesata** e il **confronto con la soglia**. Formalmente quindi:
- non vengono introdotte nuove funzioni booleane
- ogni TBN può essere simulata da una BN classica

Tuttavia, dal punto di vista della **modellazione**, le TBN risultano spesso più naturali e compatte perché rappresentano direttamente il meccanismo biologico di **integrazione dei segnali regolatori**. La traduzione in una rete booleana standard richiede in genere:
- più nodi
- funzioni di aggiornamento più complesse

Le threshold Boolean networks non aumentano quindi la potenza computazionale del formalismo, ma risultano spesso più **interpretabili e pratiche** per modellare le [[Gene Regulatory Networks (GRN)]].