---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# FeatureCounts - Software di quantificazione per RNAseq
---
**featureCounts** è un software della suite **Subread** usato nella fase di [[Analisi RNA-seq#Costruzione della matrice di conteggio|costruzione della matrice di conteggio]] della pipeline [[Analisi RNA-seq|RNA-seq]]. Prende in input reads già allineate su un riferimento, tipicamente file **SAM/BAM** prodotti da aligner come [[STAR - Software di allineamento per RNAseq|STAR]], [[HISAT2 - Software di allineamento per RNAseq|HISAT2]] o [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]], e una annotazione genomica in formato [[GFF - Formato per annotazione genomica|GTF/GFF]]. L'output principale è una matrice di **conteggi grezzi** per gene o per altra feature annotata, utilizzabile come input per strumenti di differential expression come [[DESeq2 - DE per RNAseq|DESeq2]] ed [[edgeR - DE per RNAseq|edgeR]].

featureCounts risponde alla domanda:
- "quante reads/frammenti allineati sono compatibili con ciascuna feature annotata?"

Non stima direttamente l'espressione reale di un gene, ma produce una misura proxy dell'abbondanza basata sulle reads osservate. Per questo i conteggi prodotti non sono ancora confrontabili tra campioni: devono essere normalizzati e modellati statisticamente negli step successivi della pipeline.

## Input e output

Input principali:
- file **SAM/BAM** con gli allineamenti delle reads;
- file di annotazione **GTF/GFF** con geni, esoni, trascritti o altre feature;
- parametri che definiscono il tipo di libreria e le regole di assegnazione.

Output principali:
- tabella di conteggi per feature e campione;
- statistiche di assegnazione, cioè quante reads sono state assegnate, scartate o considerate ambigue;
- informazioni sulle feature usate, come identificativo, lunghezza e coordinate.

Nel workflow gene-level tipico si contano gli **esoni** e si aggregano i conteggi a livello di **gene**. Questo si ottiene specificando:
- `-t exon`: tipo di feature da contare nel file GTF/GFF;
- `-g gene_id`: attributo usato per raggruppare più feature sotto lo stesso gene.

## Come funziona

Per ogni read, o per ogni frammento nel caso paired-end, featureCounts:
1. legge la posizione di allineamento dal file BAM/SAM;
2. confronta la regione allineata con le feature annotate;
3. valuta se l'overlap è sufficiente secondo le regole impostate;
4. controlla eventuali ambiguità, come multi-mapping o sovrapposizione a più geni;
5. assegna la read/frammento a una feature oppure la scarta;
6. incrementa il conteggio della feature assegnata.

La scelta delle regole di assegnazione è importante perché influenza direttamente la matrice finale. Due analisi con gli stessi BAM ma parametri diversi possono produrre conteggi diversi, soprattutto in regioni con geni sovrapposti, trascritti antisenso o famiglie geniche simili.

## Parametri critici

### Paired-end

Nei dati paired-end l'unità biologicamente più naturale è spesso il **frammento** di RNA/cDNA da cui derivano le due reads, non le singole reads separatamente. Con `-p`, featureCounts conta le coppie come frammenti.

Parametri utili:
- `-p`: conta frammenti paired-end invece di singole reads;
- `-B`: richiede che entrambe le reads della coppia siano allineate;
- `-C`: esclude coppie chimeriche o con mapping incoerente.

### Strandedness

Il parametro `-s` specifica se la libreria conserva l'informazione di strand:
- `-s 0`: libreria unstranded;
- `-s 1`: stranded forward;
- `-s 2`: stranded reverse.

Questo è analogo al problema del `libType` in [[Salmon - Software di allineamento per RNAseq|Salmon]]. Se la strandedness è impostata in modo errato, reads provenienti da geni sovrapposti su strand opposti possono essere assegnate male o scartate. L'effetto è particolarmente rilevante per trascritti antisenso, come discusso in [[Trascrizione del DNA]].

### Multi-mapping e overlap multipli

Una read può:
- mappare su più posizioni genomiche;
- sovrapporsi a più geni;
- cadere in regioni condivise tra isoforme o annotazioni diverse.

Per impostazione prudente, featureCounts tende a contare solo assegnazioni compatibili e non ambigue. Alcune opzioni permettono di cambiare questo comportamento:
- `-M`: include reads multi-mapping;
- `-O`: permette di assegnare una read a più feature sovrapposte;
- `--fraction`: distribuisce frazionalmente il contributo di una read tra più assegnazioni.

Queste opzioni aumentano il numero di reads assegnate, ma possono introdurre conteggi meno interpretabili. Sono utili solo se coerenti con la domanda biologica e con il modello statistico a valle.

### Qualità di mapping

Il parametro `-Q` impone una soglia minima di **MAPQ**. Una soglia più alta riduce assegnazioni incerte ma può scartare reads in regioni ripetute o difficili da mappare. Anche questa scelta influenza i conteggi finali e deve essere mantenuta costante tra campioni.

## Esempio di comando

```bash
featureCounts \
  -T 8 \
  -p -B -C \
  -s 2 \
  -t exon \
  -g gene_id \
  -a annotation.gtf \
  -o counts.txt \
  sample1.bam sample2.bam sample3.bam
```

In questo esempio:
- `-T 8` usa 8 thread;
- `-p -B -C` tratta dati paired-end e richiede coppie coerenti;
- `-s 2` indica una libreria reverse-stranded;
- `-t exon -g gene_id` conta gli esoni aggregandoli per gene;
- `counts.txt` è la matrice di conteggio gene × campioni.

## Relazione con Salmon e Kallisto

featureCounts appartiene al workflow **alignment-based**:
- prima si allineano le reads al genoma con un aligner splice-aware;
- poi si contano le reads sovrapposte alle annotazioni.

[[Salmon - Software di allineamento per RNAseq|Salmon]] e [[Kallisto - Software di allineamento per RNAseq|Kallisto]] seguono invece un approccio più orientato alla quantificazione transcript-level tramite quasi-mapping o pseudoalignment sul trascrittoma. Producono TPM e conteggi stimati, spesso aggregati poi a livello genico tramite strumenti come `tximport`.

La differenza centrale è:
- featureCounts produce conteggi discreti assegnati da allineamenti genomici;
- Salmon/Kallisto stimano abbondanze di trascritti risolvendo probabilisticamente l'ambiguità tra isoforme.

Per una DEA gene-level con [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]], featureCounts è una scelta naturale perché produce direttamente **raw counts** per gene.

## Punti di forza

- Molto veloce e scalabile, grazie all'implementazione in C e al multithreading.
- Basso uso di memoria rispetto ad approcci più lenti o interpretati.
- Adatto a molti campioni e dataset ad alta profondità.
- Supporta opzioni specifiche per RNA-seq: paired-end, strandedness, multi-mapping, conteggio gene-level o exon-level.
- Integrazione diretta con workflow di differential expression basati su conteggi grezzi.

## Limiti e rischi

- Dipende fortemente dalla qualità dell'annotazione GTF/GFF: geni mancanti o annotazioni incomplete portano a conteggi mancanti o distorti.
- Non risolve in modo probabilistico l'ambiguità tra isoforme come Salmon o Kallisto.
- Non è un toolbox generale per operazioni su intervalli genomici come BEDTools.
- Ha molti parametri: errori su strandedness, paired-end o multi-mapping possono cambiare sostanzialmente i risultati.
- Produce conteggi grezzi, non valori già normalizzati o direttamente interpretabili come espressione assoluta.

## Quando usarlo

featureCounts è indicato quando si vuole costruire rapidamente una matrice di conteggi **gene × campioni** a partire da BAM genomici, soprattutto in analisi bulk RNA-seq standard. È particolarmente adatto quando l'obiettivo downstream è la differential expression gene-level con modelli sui conteggi, come in [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]].
