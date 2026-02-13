---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# STAR - Software di allineamento per RNAseq
---
**STAR** (Spliced Transcripts Alignment to a Reference) è un software di allineamento utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 2: Alignment|Step 2: Alignment]], progettato specificamente per affrontare le problematiche tipiche del mapping di reads RNA-seq.

STAR è stato sviluppato per gestire in modo efficiente:
- rilevamento e caratterizzazione di splice junction
- allineamento di sequenze derivanti da regioni genomiche non contigue
- reads che attraversano esoni distinti

Caratteristiche principali:
- Strategia innovativa per l’allineamento delle junction:
  - particolarmente efficace nel rilevare splicing events
- Algoritmo in due fasi:
  1. **Seed search**
     - ricerca sequenziale di un *Maximum Mappable Prefix (MMP)*
     - identifica il prefisso più lungo della read che può essere mappato sul genoma
  2. **Clustering**
     - combina i seed allineati nella prima fase
     - ricostruisce l’allineamento completo della read
     - permette la gestione di gap dovuti a introni

Punti di forza:
- Elevata velocità su dataset di grandi dimensioni
- Ottima sensibilità nel rilevamento di splice junction
- Ampiamente utilizzato in pipeline bulk RNA-seq e single-cell

Considerazioni:
- Richiede un elevato uso di memoria RAM per la costruzione dell’indice genomico
- Fortemente dipendente dalla qualità del genoma di riferimento e delle annotazioni