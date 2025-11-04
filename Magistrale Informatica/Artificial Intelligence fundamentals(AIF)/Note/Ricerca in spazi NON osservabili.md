---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca in ambienti NON osservabili
---
La **ricerca in spazi [[Definizione di Problemi-Ambienti|non osservabili]]**, o s**ensorless search,** costituisce un caso in cui l’[[IMG - AIF agente.jpeg|agente]] non riceve alcuna informazione sensoriale durante l’esecuzione delle azioni. Questo tipo di problema, definito anche ***conformant search***, implica che l’agente operi in completa assenza di percezioni, affidandosi unicamente alla conoscenza delle transizioni deterministiche o non deterministiche dell’ambiente.

In tali contesti, l’agente non conosce lo stato iniziale, né può aggiornare la propria conoscenza attraverso l’osservazione. Per esempio, nel mondo dell’aspirapolvere deterministico, l’agente può partire da una condizione iniziale di completa incertezza $\{1,2,3,4,5,6,7,8\}$, in cui ogni posizione e distribuzione della polvere è possibile. Tuttavia, tramite una sequenza di azioni predeterminate, come $[\text{Right}, \text{Suck}, \text{Left}, \text{Suck}]$, l’agente riesce a raggiungere sempre lo stato obiettivo $7$. Questo processo è detto ***coercion of the world state***, poiché l’agente forza l’ambiente verso una configurazione desiderata senza mai percepirlo direttamente.
![[IMG - Ricerca in spazi NON osservabili problema vacum world.png]]

La risoluzione del problema avviene nello spazio dei **belief states**, ovvero insiemi di stati fisici coerenti con la storia delle azioni compiute. In questo spazio, il problema è **[[Definizione di Problemi-Ambienti|completamente osservabile]]**, dato che l’agente conosce sempre il proprio stato di credenza. I principali componenti della formulazione del problema in questo contesto sono:
- **Stati**: l’universo dei belief states è l’insieme delle parti degli stati fisici. Se il problema originale ha $N$ stati, ci saranno fino a $2^N$ **belief states**, sebbene molti non siano raggiungibili.
- **Stato iniziale**: in generale coincide con l’intero insieme di stati possibili, ma può essere più ristretto se l’agente ha conoscenze a priori.
- **Azioni**: assumendo un **belief state** $b=\{s_1,s_2\}$  puo succedere che $ACTIONS_P(s_1) \not= ACTIONE(s_2)$ in casi di questo tipo se le azioni illegali in uno stato non hanno effetto, si può definire $ACTIONS(b) = \bigcup_{s \in b} ACTIONS_P(s)$ in ambienti più rischiosi dove le azioni illegali possono portare a situazioni catastrofiche, si utilizza $ACTIONS(b) = \bigcap_{s \in b} ACTIONS_P(s)$.
- **Modello di transizione**:
    - Deterministico: $$
    RESULT(b, a) = \{ s' \mid s' = RESULT_P(s, a),\ s \in b \}
    $$
    - Non deterministico:$$
    RESULT(b, a) = \bigcup_{s \in b} RESULTS_P(s, a)
    $$
- **Test dell’obiettivo**: un **belief state** $b$ **possibilmente** soddisfa il **goal** se almeno uno degli stati $s \in b$ uno soddisfa $IS\text{-}GOAL_P(s)$ mente **necessariamente** solo se tutti gli stati che lo compongono soddisfano $IS\text{-}GOAL_P(s)$.
- **Costo delle azioni**: se costante in tutti gli stati, il costo si trasferisce direttamente dal problema fisico.

Questo approccio consente l’utilizzo diretto degli [[Algoritmi di ricerca non informati]] o degli [[Algoritmi di ricerca informata]], già noti per i problemi standard, applicandoli allo spazio dei **belief state**. Tuttavia, la dimensione esplosiva dello spazio $2^N$ e la complessità intrinseca nel trattare insiemi di stati rendono questo approccio poco praticabile senza tecniche di ottimizzazione.

Una strategia efficace di **pruning** consiste nell’eliminare i **belief state** che sono supersets di altri già esplorati e risolti. Questo riduce il numero di **belief state** da considerare senza sacrificare la correttezza. nonostante questo questo approccio non migliora a abbastanza per renderlo fattibile.

Un’ulteriore alternativa agli algoritmi di ricerca standard è l’approccio incrementale (***incremental belief-state search***), in cui si costruisce una soluzione valida per ciascun stato fisico all’interno del **belief state**, uno alla volta. A differenza della [[Alberi di ricerca AND-OR|Ricerca AND-OR]], che permette strategie condizionali differenziate per ciascun ramo, questa tecnica richiede un’unica sequenza di azioni valida per tutti gli stati considerati. Tale metodo consente di individuare rapidamente insiemi non risolvibili, spesso rilevando inconsistenze dopo pochi stati esaminati, con un conseguente significativo risparmio computazionale.


