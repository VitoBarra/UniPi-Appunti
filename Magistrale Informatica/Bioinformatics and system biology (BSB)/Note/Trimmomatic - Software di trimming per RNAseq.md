---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Trimmomatic - Software di trimming per RNAseq
---
**Trimmomatic** è un software di trimming utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]], progettato per eseguire in modo modulare più operazioni di filtraggio e pulizia delle reads.

Trimmomatic combina diversi step di preprocessing in una pipeline configurabile.

Strengths:
- Pipeline-style trimming:
  - adapter clipping
  - sliding-window quality trimming
  - cropping
  - filtri su lunghezza minima
  - ordine dei moduli configurabile
- Ragionevolmente veloce e multithreaded:
  - scritto in Java
  - ampiamente utilizzato in pipeline RNA-seq Illumina
- Ampio supporto:
  - integrato in numerosi wrapper, GUI e tutorial
  - molto diffuso in pipeline consolidate

Weaknesses:
- Più lento e meno feature-rich rispetto a tool moderni “all-in-one”:
  - fastp è tipicamente 2–5× più veloce
  - fastp integra QC e filtri aggiuntivi in un singolo passaggio
- Logica adattatori meno flessibile:
  - utilizza file FASTA di adattatori
  - matching meno sofisticato rispetto a [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] o [[Atropos - Software di trimming per RNAseq|Atropos]] per configurazioni complesse

Best for:
- Pipeline legacy o già stabilizzate
- Workflow modulari e facilmente leggibili
- Utenti che preferiscono uno schema di trimming semplice e parametrico

