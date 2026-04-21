---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# MultiQC - Report aggregato per RNAseq
---
**MultiQC** è un software di aggregazione dei report utilizzato nella pipeline di [[Analisi RNA-seq|analisi RNA-seq]] per riassumere in un'unica dashboard i risultati prodotti da molti tool bioinformatici, tra cui [[FASTQC - Report di qualità per RNAseq|FASTQC]].

A differenza di FASTQC, che analizza il singolo campione, MultiQC non calcola nuove metriche sui reads: raccoglie e organizza automaticamente gli output già prodotti da altri software.

![video tutorial](https://www.youtube.com/watch?v=qPbIlO_KWN0)

## Perché è utile
Quando un esperimento contiene molti campioni, leggere separatamente decine di report diventa poco pratico. MultiQC permette di:
- confrontare rapidamente la qualità tra campioni diversi
- individuare outlier o campioni problematici
- evidenziare possibili batch effects tecnici già nelle fasi iniziali
- riassumere il confronto *before trimming* vs *after trimming*
- produrre una vista globale e standardizzata dell'intero dataset

## Input e output
MultiQC prende in input una cartella contenente report generati da altri strumenti e produce tipicamente:
- un report `HTML` unico e interattivo
- un insieme di file tabellari riassuntivi

Può integrare output provenienti da tool diversi, ad esempio:
- [[FASTQC - Report di qualità per RNAseq|FASTQC]] per il quality control
- software di trimming come [[Cutadapt - Software di trimming per RNAseq|Cutadapt]], [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[fastp - Software di trimming per RNAseq|fastp]]
- software di allineamento o quantificazione nelle fasi successive della pipeline

## Come leggere MultiQC
MultiQC non sostituisce i report originali, ma li rende confrontabili. Il suo valore principale è la lettura trasversale tra campioni.

Nel contesto RNA-seq, è utile osservare soprattutto:
- campioni con andamento qualitativo molto diverso dagli altri
- presenza sistematica di adattatori o calo di qualità in più campioni
- differenze marcate tra campioni prima e dopo trimming
- pattern coerenti con un possibile problema di batch o di preparazione della libreria

Se MultiQC mostra un campione chiaramente anomalo, conviene poi tornare al report originale del tool sorgente, ad esempio [[FASTQC - Report di qualità per RNAseq|FASTQC]], per un'ispezione più dettagliata.

## Relazione con FASTQC
FASTQC e MultiQC sono complementari:
- **FASTQC** analizza il singolo file [[Formato FASTQ|FASTQ]] e produce metriche diagnostiche locali
- **MultiQC** aggrega molti report FASTQC e li presenta in forma comparativa

Per questo motivo, MultiQC è particolarmente utile quando il numero di campioni cresce e serve una valutazione coerente dell'intero esperimento.