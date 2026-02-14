---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# ChIP-seq
---
La **ChIP-seq (Chromatin Immunoprecipitation sequencing)** è una tecnica sperimentale utilizzata per identificare le regioni del [[DNA Struttura e funzionalità|DNA]] a cui si legano specifiche proteine regolatorie, in particolare i **transcription factors**.

La tecnica permette quindi di individuare possibili relazioni regolatorie tra transcription factors e geni target.

Il principio dell’esperimento consiste nell’identificare frammenti di DNA che risultano legati a una specifica [[Proteine|proteina]].

Le principali fasi dell’esperimento sono:
- **cross-linking** tra DNA e proteine per fissare le interazioni presenti nella cellula
- **frammentazione del DNA** in piccoli segmenti
- **immunoprecipitazione** utilizzando anticorpi specifici per la proteina di interesse
- **sequenziamento** dei frammenti di DNA recuperati
- **allineamento** delle sequenze al genoma di riferimento
Se molti frammenti sequenziati si allineano in una specifica regione del genoma, quella regione rappresenta un possibile **binding site** per il **transcription factor**.

Se il binding site si trova in prossimità della regione promotrice di un gene $g$, è possibile ipotizzare una relazione regolatoria tra il transcription factor $TF$ e il gene target.

Le informazioni ottenute da ChIP-seq sono quindi spesso utilizzate per:
- identificare **target genes** di transcription factors
- restringere lo spazio delle interazioni candidate nella [[GRN - inferenza|inferenza delle GRN]]
- integrare dati di espressione genica con evidenze sperimentali di legame DNA-proteina

![[IMG - ChIP-seq.png]]
[videofonte](https://www.youtube.com/watch?v=nkWGmaYRues)