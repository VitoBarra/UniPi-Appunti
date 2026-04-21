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
**AdapterRemoval v2** è un software di **trimming** utilizzato nella [[Analisi RNA-seq|analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: sequence trimming]]. Il suo punto di forza è la gestione integrata di trimming degli adattatori e merging di reads paired-end sovrapposte.

AdapterRemoval v2 lavora direttamente sui file [[Formato FASTQ|FASTQ]] e produce reads trimmate, con particolare efficacia nei dataset in cui molte reads paired-end si sovrappongono.

AdapterRemoval v2 viene usato soprattutto per:
- rimuovere adattatori
- eseguire trimming delle reads paired-end
- fondere reads paired-end sovrapposte in una singola sequenza
- filtrare reads in base a criteri di lunghezza e qualità
- gestire in modo integrato trimming e merging

Il suo obiettivo è ripulire il dataset e sfruttare la sovrapposizione tra reads paired-end quando questa contiene informazione utile.

AdapterRemoval v2 prende tipicamente in input file [[Formato FASTQ|FASTQ]] paired-end e produce:
- file FASTQ trimmati
- reads merged quando la sovrapposizione lo consente
- reads non merged mantenute separate

In una pipeline tipica il flusso è:
[[FASTQC - Report di qualità per RNAseq|FASTQC]] -> [[MultiQC - Report aggregato per RNAseq|MultiQC]] -> **AdapterRemoval v2** -> nuovo [[FASTQC - Report di qualità per RNAseq|FASTQC]] -> nuovo [[MultiQC - Report aggregato per RNAseq|MultiQC]] -> allineamento

Questo permette di verificare se il trimming ha ridotto adattatori residui e se il merging ha migliorato la qualità dei frammenti ricostruiti.

##### **Punti di forza**
I principali punti di forza di AdapterRemoval v2 sono:
- ottima gestione di reads paired-end sovrapposte
- trimming e merging nello stesso workflow
- buona velocità su dataset ad alto throughput
- utilità particolare in librerie con inserti corti

È particolarmente efficace quando la sovrapposizione tra le due reads della coppia è informativa e consente di ricostruire meglio il frammento originario.

##### **Limiti**
AdapterRemoval v2 ha anche alcuni limiti:
- è più focalizzato di tool generalisti di preprocessing
- non è orientato alla produzione di report QC ricchi come [[FASTQC - Report di qualità per RNAseq|FASTQC]]
- perde parte del suo vantaggio quando il merging paired-end non è rilevante

In dataset senza vera sovrapposizione tra reads, strumenti come [[Cutadapt - Software di trimming per RNAseq|Cutadapt]], [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[fastp - Software di trimming per RNAseq|fastp]] possono risultare più naturali da usare.

##### **Quando usarlo**
AdapterRemoval v2 è particolarmente adatto quando:
- lavori con reads paired-end che si sovrappongono spesso
- hai librerie con inserti corti
- vuoi integrare trimming e merging nello stesso passaggio
- vuoi sfruttare la ricostruzione di frammenti merged prima dell'allineamento

Nel confronto con altri strumenti:
- [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] offre più controllo fine sulla logica di trimming degli adattatori
- [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] è più modulare come pipeline classica di trimming
- [[fastp - Software di trimming per RNAseq|fastp]] è più integrato come preprocessing rapido con QC incluso

##### **Interpretazione nella pipeline**
L'uso di AdapterRemoval v2 ha senso soprattutto quando i report di [[FASTQC - Report di qualità per RNAseq|FASTQC]] o la conoscenza del design sperimentale suggeriscono:
- presenza di adattatori residui
- reads paired-end con probabile sovrapposizione
- inserti corti rispetto alla lunghezza delle reads

Dopo il preprocessing con AdapterRemoval v2 ci si aspetta tipicamente:
- riduzione del contenuto di adattatori
- miglioramento della qualità terminale
- possibile generazione di reads merged più informative
- riduzione del numero di reads inutilizzabili o troppo corte
