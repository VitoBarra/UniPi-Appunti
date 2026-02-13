---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# AdapterRemoval v2 - Software di trimming per RNAseq
---
**AdapterRemoval v2** è un software di trimming utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]], particolarmente ottimizzato per la gestione e il merging di reads paired-end sovrapposte.

AdapterRemoval v2 è progettato per scenari in cui il merging delle reads è centrale, come librerie con inserti corti o DNA degradato.

Strengths:
- Eccellente per overlapping paired-end reads:
  - altissimo merge rate
  - molto veloce nei benchmark di merging
  - particolarmente adatto a inserti corti o DNA degradato
- Funzionalità avanzate sugli adattatori:
  - gestione di più coppie di adattatori nello stesso dataset
  - demultiplexing + trimming simultanei
  - ricostruzione di adattatori sconosciuti da reads sovrapposte
- Alto throughput:
  - utilizza SIMD e multithreading
  - tra i più veloci in diversi test comparativi

Weaknesses:
- Tool focalizzato, meno funzionalità accessorie:
  - nessun report HTML QC integrato (tipicamente combinato con [[FASTQC - Report di qualità per RNAseq|FASTQC]])
  - nessuna visualizzazione avanzata
- Non sempre il più veloce nel trimming “puro”:
  - in dataset senza necessità di merging, tool come [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] possono risultare competitivi
  - meno orientato a workflow “all-in-one” rispetto a [[fastp - Software di trimming per RNAseq|fastp]]

Best for:
- Librerie con inserti corti o DNA degradato
- Progetti in cui il merging paired-end è un passaggio centrale
- Pipeline in cui trimming e merging devono essere eseguiti in modo integrato con lo [[analisi RNA-seq]]
