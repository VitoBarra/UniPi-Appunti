---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - inferenza
---
**L’inferenza** delle [[Gene Regulatory Networks (GRN)|GRN]] consiste nel ricostruire la struttura delle interazioni regolatorie tra geni a partire da dati sperimentali. Poiché le interazioni regolatorie non sono completamente note, vengono utilizzati metodi computazionali per stimare quali geni influenzano l’espressione di altri geni.

Formalmente, data una rete con $n$ geni, il problema consiste nello stimare una matrice di adiacenza regolatoria$$A=(a_{ij})$$dove $a_{ij}$ rappresenta l’influenza del gene $i$ sull’espressione del gene $j$.

I dati utilizzati per l’inferenza derivano principalmente da esperimenti di espressione genica e da tecniche sperimentali che identificano possibili relazioni regolatorie.

Le principali fonti di dati includono:
- **gene expression data** ottenuti da [[Analisi RNA-seq|RNA-seq]] o microarray
- **gene expression time-series** che misurano l’espressione genica in diversi istanti temporali
- informazioni sui **transcription factors**
- esperimenti di **knock-out o knock-down**
- dati di legame DNA-proteina come **[[ChIP-seq|ChIP-seq]]**
- dati sulla **accessibilità della cromatina**

I dati di espressione genica sono tipicamente organizzati in una **expression matrix**
$$X\in\mathbb{R}^{m\times n}$$
dove:
- $m$ è il numero di esperimenti o condizioni
- $n$ è il numero di geni
- $x_{ij}$ rappresenta il livello di espressione del gene $j$ nell’esperimento $i$

Prima dell’analisi è generalmente necessario effettuare una fase di **pre-processing** dei dati per ridurre il rumore sperimentale. Le operazioni più comuni includono:
- **normalizzazione** dei livelli di espressione
- trasformazione logaritmica $x\rightarrow \log(x)$ per ridurre la skewness della distribuzione
- rimozione di geni con **bassa varianza**, che non forniscono informazione regolatoria
- eliminazione di **outlier sperimentali**

una fonte importante di informazione è costituita dagli esperimenti [[ChIP-seq]]. Questi permettono di identificare le regioni del [[DNA Struttura e funzionalità|DNA]] a cui si legano specifiche [[Proteine|proteine]] regolatrici, fornendo quindi evidenza diretta dei possibili geni target di un [[Transcription Factor (TF)|transcription factor]]. Utilizzare i **[[Transcription Factor (TF)|transcription factors (TF)]]** come possibili regolatori consente di restringere lo spazio delle interazioni da stimare nelle **procedure di inferenza delle GRN**. Infatti Invece di considerare tutte le possibili coppie di geni, si assume che le regolazioni abbiano tipicamente la forma: $$TF_i \rightarrow g_j$$Se $T$ è l’insieme dei **transcription factors** e $G$ l’insieme di tutti i geni, il numero di interazioni candidate diventa:$$T \times G$$invece di $G \times G$.


Un altro tipo di dato molto informativo deriva da esperimenti di **[[Knock-out and Mutation Analysis|knock-out o knock-down]],** in cui l’attività di un gene viene eliminata o ridotta. Confrontando il profilo di espressione nel sistema **wild-type** con quello ottenuto dopo il knock-out, è possibile identificare geni influenzati da quello disattivato. Se $x_j^{WT}$ rappresenta l’espressione del gene $j$ nel wild-type e $x_j^{KO(i)}$ quella osservata dopo il knock-out del gene $i$, una variazione significativa$$x_j^{KO(i)} \neq x_j^{WT}$$indica che il gene $j$ è influenzato direttamente o indirettamente da $i$.


I dati di espressione possono essere raccolti in due modalità principali.
misura i livelli di espressione dei geni in diversi campioni o condizioni sperimentali indipendenti. Questo tipo di dato permette di identificare relazioni di **co-espressione**, ma non fornisce direttamente informazioni sulla causalità.

**Gene expression time-series**  
misura l’espressione genica in diversi istanti temporali dopo una perturbazione del sistema. In questo caso è possibile osservare relazioni temporali tra geni e inferire possibili relazioni causali.

Se $x_i(t)$ rappresenta l’espressione del gene $i$ al tempo $t$, una possibile relazione regolatoria può manifestarsi come
$$x_j(t+\Delta t)=f(x_i(t))$$
dove l’attivazione del gene $i$ precede quella del gene $j$.

Tuttavia, le **time-series** sono molto meno comuni dei dati steady-state perché richiedono esperimenti più complessi e costosi.

A partire da questi dati sono stati sviluppati diversi approcci computazionali per inferire reti regolatorie. Le principali famiglie di metodi includono:
- **correlation / co-expression networks**, basati su correlazioni statistiche tra profili di espressione
- **[[Bayesian network|Bayesian networks]]**, che modellano dipendenze condizionali tramite grafi diretti aciclici
- **metodi information-theoretic**, basati su misure di dipendenza come la [[Mutual Information (MI)|mutual information]] ad esempio [[GRN - inferenza - ARACNE|ARACNE]]
- **metodi di machine learning**, che formulano l’inferenza come problemi predittivi come [[GRN - inferenza - GENIE3|GENIE3]]
Il risultato dell’inferenza è tipicamente una rete regolatoria diretta e pesata che rappresenta una stima della struttura della [[Gene Regulatory Networks (GRN)|GRN]].

