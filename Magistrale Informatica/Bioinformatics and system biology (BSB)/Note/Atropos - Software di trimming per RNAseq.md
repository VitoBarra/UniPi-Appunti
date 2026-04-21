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
**Atropos** è un software di **trimming** utilizzato nella [[Analisi RNA-seq|analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]]. Il suo ruolo principale è offrire trimming flessibile degli adattatori con funzionalità avanzate e buone prestazioni.

Atropos deriva da [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] e ne mantiene la logica generale, aggiungendo ottimizzazioni e modalità operative più ricche.

Atropos viene usato soprattutto per:
- rimuovere adattatori `3'` e `5'`
- eseguire quality trimming delle reads
- filtrare reads in base a lunghezza e qualità
- gestire strategie di trimming più avanzate
- supportare workflow ad alto volume di dati

Il suo obiettivo è combinare controllo fine del trimming e prestazioni migliori rispetto a strumenti più essenziali.

Atropos prende tipicamente in input file [[Formato FASTQ|FASTQ]] grezzi e produce nuovi file FASTQ trimmati.

In una pipeline tipica il flusso è:
[[FASTQC - Report di qualità per RNAseq|FASTQC]] -> [[MultiQC - Report aggregato per RNAseq|MultiQC]] -> **Atropos** -> nuovo [[FASTQC - Report di qualità per RNAseq|FASTQC]] -> nuovo [[MultiQC - Report aggregato per RNAseq|MultiQC]] -> allineamento

Questo permette di verificare se moduli come `Adapter content` o `Per base sequence quality` migliorano dopo il trimming.

##### **Punti di forza**
I principali punti di forza di Atropos sono:
- elevata flessibilità nella gestione degli adattatori
- buone prestazioni in termini di velocità
- opzioni avanzate per strategie di trimming diverse
- utilità in pipeline con grandi volumi di dati

Atropos è particolarmente interessante quando vuoi mantenere la logica di [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] ma con un set di opzioni più esteso.

##### **Limiti**
Atropos ha anche alcuni limiti:
- è meno diffuso di [[Cutadapt - Software di trimming per RNAseq|Cutadapt]], [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[fastp - Software di trimming per RNAseq|fastp]]
- ha una base utenti più ridotta e quindi meno tutorial, wrapper e casi d'uso standardizzati
- può risultare meno immediato in ambienti in cui si preferiscono strumenti molto semplici o binari standalone

##### **Quando usarlo**
Atropos è particolarmente adatto quando:
- vuoi trimming flessibile e fine controllo degli adattatori
- vuoi una soluzione vicina a [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] ma con opzioni aggiuntive
- lavori con dataset grandi e vuoi buone prestazioni
- hai bisogno di modalità di trimming meno standard o più sofisticate

Nel confronto con altri strumenti:
- [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] resta il riferimento più noto per trimming flessibile degli adattatori
- [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] è più leggibile come pipeline classica modulare
- [[fastp - Software di trimming per RNAseq|fastp]] è più integrato e rapido come soluzione all-in-one

##### **Interpretazione nella pipeline**
L'uso di Atropos ha senso soprattutto quando i report di [[FASTQC - Report di qualità per RNAseq|FASTQC]] mostrano segnali come:
- adattatori residui
- code terminali a bassa qualità
- necessità di trimming configurabile in modo dettagliato

Dopo il trimming con Atropos, ci si aspetta tipicamente:
- riduzione del contenuto di adattatori
- miglioramento della qualità nelle regioni terminali
- riduzione del numero di reads troppo corte o troppo degradate
- maggiore controllo sulla logica di preprocessing rispetto a strumenti più automatici
