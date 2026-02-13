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
**Cutadapt** è un software di **trimming** utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]], con focus specifico sulla rimozione di adattatori e trimming mirato delle reads.

Cutadapt non esegue analisi di qualità avanzate, ma si concentra sulla rimozione accurata delle sequenze di adattatore e su strategie di trimming configurabili.

Strengths:
- Gestione estremamente flessibile degli adattatori:
  - supporto per adattatori 5' e 3'
  - adattatori ancorati
  - adattatori linked
  - adattatori di lunghezza variabile
  - modalità overlapping
- Elevata accuratezza di trimming:
  - alta sensibilità nella rimozione delle vere sequenze adattatrici
- Software maturo e ben documentato:
  - ampia diffusione
  - documentazione dettagliata
  - numerosi esempi d’uso nella comunità

Weaknesses:
- Non è tra i più veloci:
  - generalmente più lento rispetto a tool in C++ come fastp
  - spesso più lento di BBDuk o Trimmomatic in benchmark orientati alla velocità
- Scope ristretto:
  - focalizzato sul trimming
  - non genera report QC completi
  - gestione UMI e filtri avanzati richiedono strumenti aggiuntivi o scripting

Best for:
- Massimo controllo sulla logica di trimming
- Configurazioni di adattatori non standard o complesse
- Pipeline in cui si desidera separare rigorosamente:
  - QC (es. FASTQC)
  - trimming (Cutadapt)
  - analisi downstream (alignment, quantificazione, DE)