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
**Trimmomatic** è un software di **trimming** utilizzato nella [[Analisi RNA-seq|analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]]. Il suo ruolo principale è applicare in modo modulare diverse operazioni di filtraggio e pulizia delle reads.

Trimmomatic lavora direttamente sui file [[Formato FASTQ|FASTQ]] e produce nuovi file [[Formato FASTQ|FASTQ]] trimmati, più adatte alle fasi successive di allineamento, quantificazione e analisi a valle.

Trimmomatic viene usato soprattutto per:
- rimuovere adattatori
- eseguire quality trimming con finestre scorrevoli
- tagliare basi alle estremità delle reads
- filtrare reads troppo corte
- concatenare più operazioni in una pipeline configurabile
Il suo obiettivo è ripulire il dataset in modo modulare, applicando una sequenza controllata di filtri e trasformazioni.

##### **Punti di forza**
I principali punti di forza di Trimmomatic sono:
- struttura modulare e leggibile
- possibilità di concatenare più step di trimming
- ampia diffusione in pipeline consolidate
- buon supporto per workflow Illumina classici

Trimmomatic è spesso usato perché permette di costruire pipeline di trimming facili da leggere, in cui ogni passaggio è esplicito.

##### **Limiti**
Trimmomatic ha anche alcuni limiti:
- offre meno flessibilità di [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] nella gestione di adattatori complessi
- è meno integrato di [[fastp - Software di trimming per RNAseq|fastp]] sul lato QC e preprocessing “all-in-one”
- può risultare più verboso da configurare quando si vogliono molte operazioni insieme

##### **Quando usarlo**
Trimmomatic è particolarmente adatto quando:
- vuoi una pipeline di trimming modulare e trasparente
- lavori in workflow già consolidati o legacy
- vuoi concatenare esplicitamente adapter clipping, quality trimming e filtri di lunghezza
- preferisci una logica di preprocessing semplice e parametrica

Nel confronto con altri strumenti:
- [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] offre più controllo fine sul matching degli adattatori
- [[fastp - Software di trimming per RNAseq|fastp]] integra trimming e QC in un unico strumento più rapido
- [[Atropos - Software di trimming per RNAseq|Atropos]] estende l'approccio di Cutadapt con funzionalità aggiuntive

##### **Interpretazione nella pipeline**
L'uso di Trimmomatic ha senso soprattutto quando i report di [[FASTQC - Report di qualità per RNAseq|FASTQC]] mostrano segnali come:
- presenza di adattatori residui nel modulo `Adapter content`
- calo della qualità verso le estremità delle reads
- reads che richiedono trimming e filtraggio in più passaggi distinti

Dopo il trimming con Trimmomatic, ci si aspetta tipicamente:
- riduzione degli adattatori residui
- miglioramento della qualità terminale delle reads
- riduzione della lunghezza di una parte delle reads
- eliminazione di reads troppo corte o troppo degradate
