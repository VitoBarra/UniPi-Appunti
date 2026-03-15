---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - inferenza con transcriptor factor noti
---
inferenza con transcription factor noti descrive un approccio di [[GRN - inferenza|inferenza delle Gene Regulatory Networks]] in cui si sfrutta la conoscenza preventiva dei [[Transcription Factor (TF)|transcription factor]], solitamente ottenuta tramite [[ChIP-seq|ChIP-seq]], per restringere lo spazio delle possibili interazioni tra geni.
Conoscendo i trasncription factor si possono ignorare le interazioni **target-gene->target-gene** e si conisiderano solo le influenze **TF->TF** e **TF->target-gete** ![[IMG - count matrix to GRN.png]]
Per ogni gene target si cerca quindi di identificare quali **transcription factor** spiegano meglio il suo livello di espressione nelle diverse condizioni. Dato un gene target $g_j$ si considerano i profili di espressione dei transcription factor: $$g_j = f(TF_1,TF_2,\dots,TF_k)$$dove $f$ è una funzione che misura l’influenza dei regolatori sul target.

In pratica l’algoritmo calcola uno **score di regolazione** per ogni coppia $(TF_i, g_j)$: $$w_{ij}$$che rappresenta la forza della possibile relazione regolatoria.
![[IMG - construzione GRD da counting matrix.gif]]
Una volta calcolati gli score per tutte le coppie possibili, si costruisce la rete selezionando solo le interazioni più significative.

Questo può essere fatto:
- fissando una soglia $\theta$ e si mantengono gli archi $TF_i \rightarrow g_j \quad \text{se} \quad w_{ij} > \theta$
- oppure selezionando i **top-k archi** con score maggiore.
La presenza dei **[[Transcription Factor (TF)|transcription factor]]** come possibili nodi sorgente permette di migliorare la qualità dell’inferenza e di ottenere reti più biologicamente plausibili.
![[IMG - selezione edge migliori costruzione di GRN.png]]
