---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# fastp - Software di trimming per RNAseq 
---
**fastp** è un software di preprocessing e **trimming** utilizzato nella [[Analisi RNA-seq|analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: quality assessment and sequence trimming]]. Il suo ruolo principale è combinare in un unico strumento trimming, filtering e controllo qualità di base.

fastp lavora direttamente sui file [[Formato FASTQ|FASTQ]] e produce reads trimmate insieme a report diagnostici che permettono di valutare rapidamente il risultato del preprocessing.

**fastp** viene usato soprattutto per:
- rimuovere adattatori
- eseguire quality trimming delle reads
- filtrare reads troppo corte o troppo rumorose
- correggere alcuni errori nei dati paired-end
- produrre report QC in formato `HTML` e `JSON`
Il suo obiettivo è concentrare in un solo passaggio molte operazioni che in altre pipeline vengono separate tra trimming e quality control.

fastp prende tipicamente in input file [[Formato FASTQ|FASTQ]] grezzi e produce:
- nuovi file FASTQ trimmati
- un report `HTML`
- un report `JSON`

##### **Nota sui dati paired-end**
Nei dataset paired-end, fastp riceve due file che rappresentano le due reads della stessa coppia:
- `R1` o `_1`
- `R2` o `_2`

Questi due file non rappresentano due campioni diversi, ma le due estremità dello stesso frammento sequenziato. Per questo motivo, quando si lavora in paired-end, fastp dovrebbe processare le due reads insieme e non come file indipendenti.

Questo è importante perché:
- mantiene coerente l'associazione tra le due reads della coppia
- evita che un file venga filtrato o trimmato con logica separata dall'altro
- preserva un output corretto per gli step successivi della pipeline

In pratica, nei dati paired-end, il trimming non va pensato come "pulizia di due file separati", ma come preprocessing congiunto di coppie di reads.

In una pipeline tipica può essere usato in due modi:
- come tool unico di preprocessing rapido, prima dell'allineamento
- come alternativa più integrata a una pipeline del tipo [[FASTQC - Report di qualità per RNAseq|FASTQC]] -> trimming -> nuovo [[FASTQC - Report di qualità per RNAseq|FASTQC]]

##### **Punti di forza**
I principali punti di forza di fastp sono:
- elevata velocità
- integrazione di molte operazioni in un unico comando
- generazione automatica di report QC
- supporto pratico per dataset Illumina standard

fastp è particolarmente apprezzato perché unisce:
- trimming degli adattatori
- quality filtering
- trimming di code problematiche
- stima rapida di metriche di qualità

Questo lo rende molto comodo quando si vuole un preprocessing rapido, semplice e già corredato da diagnostica.

##### **Limiti**
fastp ha anche alcuni limiti:
- offre meno controllo fine sulla logica di trimming rispetto a [[Cutadapt - Software di trimming per RNAseq|Cutadapt]]
- può spingere a usare impostazioni automatiche senza analizzare abbastanza il dataset
- per design di adattatori complessi o non standard può essere meno flessibile di strumenti più specializzati

##### **Quando usarlo**
fastp è particolarmente adatto quando:
- vuoi un preprocessing rapido in un solo comando
- lavori con dati Illumina short-read abbastanza standard
- vuoi trimming e QC integrati senza separare molti tool
- vuoi una soluzione pratica per pipeline snelle e riproducibili

Nel confronto con altri strumenti:
- [[Cutadapt - Software di trimming per RNAseq|Cutadapt]] offre più controllo fine sulla logica di adattatori
- [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] è più modulare come pipeline classica di trimming

##### **Interpretazione nella pipeline**
L'uso di fastp ha senso quando si vuole correggere rapidamente problemi come:
- adattatori residui
- code terminali a bassa qualità
- reads troppo corte o troppo rumorose

Dopo il preprocessing con fastp ci si aspetta tipicamente:
- riduzione degli adattatori residui
- miglioramento della qualità terminale delle reads
- rimozione di reads peggiori o troppo corte
- disponibilità immediata di un report QC per confronto e verifica
