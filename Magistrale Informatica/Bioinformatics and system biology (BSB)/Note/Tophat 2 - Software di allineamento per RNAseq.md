---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Tophat 2 - Software di allineamento per RNAseq
---
**Tophat 2** è un software di allineamento utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 2: Alignment|Step 2: Alignment]], sviluppato per affrontare in modo esplicito il problema delle splice junction nelle reads RNA-seq.

Tophat 2 utilizza [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]] come motore di allineamento di base, estendendolo con una logica specifica per la rilevazione di giunzioni introniche.

Principi operativi:
- Focalizzato sulla gestione di reads che attraversano più esoni.
- Dipendenza diretta da [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]] per l’allineamento primario.

Strategia di allineamento:
1. Mapping iniziale:
   - le reads vengono allineate al genoma con [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]]
   - le reads che si allineano su più esoni vengono trattate come non mappate
2. Frammentazione:
   - le reads non mappate vengono suddivise in frammenti più piccoli
   - ciascun frammento viene riallineato al genoma
3. Identificazione delle splice junction:
   - la distanza tra frammenti allineati suggerisce possibili regioni di splicing
   - le sequenze genomiche attorno a tali regioni vengono concatenate
   - le nuove sequenze “spliced” sono considerate potenziali trascritti
4. Riallineamento finale:
   - reads non mappate o scarsamente mappate vengono riallineate contro queste sequenze ricostruite

Caratteristiche:
- Progettato specificamente per RNA-seq splice-aware
- Consente identificazione di nuove splice junction
- Architettura modulare basata su Bowtie2

Limitazioni:
- Superato in velocità ed efficienza da aligner più recenti come [[STAR - Software di allineamento per RNAseq|STAR]] e [[HISAT2 - Software di allineamento per RNAseq|HISAT2]]
- Maggiore complessità computazionale rispetto a soluzioni più moderne