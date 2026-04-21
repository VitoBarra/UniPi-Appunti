---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Cutadapt - Software di trimming per RNAseq 
---
**Cutadapt** è un software di **trimming** utilizzato nella [[Analisi RNA-seq|analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]]. Il suo ruolo principale è rimuovere adattatori e tagliare in modo mirato le reads prima delle fasi successive della pipeline.

Cutadapt lavora direttamente sui file [[Formato FASTQ|FASTQ]] e produce nuovi file [[Formato FASTQ|FASTQ]] trimmati, più adatte alle fasi di [[Bowtie2 - Software di allineamento per RNAseq|allineamento]], quantificazione e analisi a valle.

Cutadapt viene usato soprattutto per:
- rimuovere adattatori `3'` e `5'`
- eseguire trimming di basi terminali indesiderate
- filtrare reads troppo corte dopo il trimming
- eliminare o conservare reads in base a criteri configurabili

Il suo obiettivo è ridurre l'impatto di sequenze tecniche residue e di regioni terminali problematiche sulle analisi successive.


##### **Punti di forza**
I principali punti di forza di Cutadapt sono:
- gestione molto flessibile degli adattatori
- trimming accurato anche in configurazioni non standard
- ampia diffusione e documentazione matura

In particolare supporta:
- adattatori `5'` e `3'`
- adattatori ancorati
- adattatori linked
- adattatori di lunghezza variabile
- modalità di matching sovrapposto

Cutadapt è quindi adatto quando serve massimo controllo sulla logica di trimming e quando la libreria non segue uno schema [[Illumina - Tecnica di sequenziamento|Illumina]] del tutto standard.

##### **Limiti**
Cutadapt ha anche alcuni limiti:
- è focalizzato sul trimming e non concentra tutto il preprocessing in un unico comando
- non produce da solo report QC completi come quelli di [[FASTQC - Report di qualità per RNAseq|FASTQC]]
- può essere meno rapido di strumenti molto ottimizzati in C++

##### **Quando usarlo**
Cutadapt è particolarmente adatto quando:
- vuoi rimuovere adattatori in modo esplicito e controllato
- hai design di adattatori complessi o non standard
- vuoi separare in modo netto la fase di QC dalla fase di trimming
- vuoi un controllo più fine rispetto a tool come [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[fastp - Software di trimming per RNAseq|fastp]]

Nel confronto con altri strumenti:
- [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] è più modulare come pipeline generale di trimming
- [[fastp - Software di trimming per RNAseq|fastp]] è più integrato e veloce, con QC incorporato
- [[Atropos - Software di trimming per RNAseq|Atropos]] estende l'idea di Cutadapt con alcune funzionalità aggiuntive

##### **Interpretazione nella pipeline**
L'uso di Cutadapt ha senso soprattutto quando i report di [[FASTQC - Report di qualità per RNAseq|FASTQC]] mostrano segnali come:
- presenza di adattatori residui nel modulo `Adapter content`
- code terminali a bassa qualità in `Per base sequence quality`
- sequenze sovrarappresentate riconducibili ad adattatori o artefatti tecnici

Dopo il trimming, ci si aspetta tipicamente:
- riduzione del contenuto di adattatori
- miglioramento della qualità nelle regioni terminali
- possibile riduzione della lunghezza media delle reads
- possibile perdita di reads troppo corte o troppo degradate
