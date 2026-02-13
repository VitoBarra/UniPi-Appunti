---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Atropos - Software di trimming per RNAseq
---
**Atropos** è un software di trimming utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]], progettato come estensione avanzata di [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] con miglioramenti in termini di velocità e funzionalità.

Atropos è un fork di Cutadapt e ne mantiene la flessibilità nella gestione degli adattatori, aggiungendo ottimizzazioni e nuove modalità operative.

Strengths:
- Alta accuratezza + velocità:
  - fino a ~4× maggiore accuratezza di trimming
  - ~50% riduzione del runtime con 16 thread rispetto ad altri trimmer state-of-the-art
- “Cutadapt con potenziamenti”:
  - stessa flessibilità nella specifica degli adattatori
  - migliore multithreading
  - algoritmi aggiuntivi
  - modellazione degli errori
- Opzioni avanzate:
  - supporto per dati bisulfite
  - diverse strategie di quality trimming
  - adatto a esperimenti di sequenziamento ad alto volume

Weaknesses:
- Base utenti più ridotta:
  - meno standard rispetto a [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]], [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] o [[fastp - Software di trimming per RNAseq|fastp]]
  - meno tutorial e wrapper disponibili
- Installazione basata su Python:
  - ambiente più pesante rispetto a binari statici (es. [[fastp - Software di trimming per RNAseq|fastp]])
  - potenzialmente meno pratico in ambienti HPC

Best for:
- Utenti che apprezzano la flessibilità di [[Cutadapt - Software di trimming per RNAseq|Cutadapt]]
- Pipeline che richiedono modalità di trimming avanzate
- Situazioni in cui è necessario bilanciare controllo fine e performance migliorate
