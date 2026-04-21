---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# BEDTools - Software di quantificazione per RNAseq
---
**BEDTools** è una suite generale per operazioni su **intervalli genomici**. Nel contesto [[Analisi RNA-seq|RNA-seq]] può essere usata nella fase di [[Analisi RNA-seq#Costruzione della matrice di conteggio|costruzione della matrice di conteggio]], ma non nasce come software specializzato per contare reads gene-level. È più corretto considerarla una toolbox per confrontare, intersecare, fondere e misurare regioni genomiche.

BEDTools risponde a domande del tipo:
- "quante reads o basi coperte cadono dentro queste regioni genomiche?"
- "quali intervalli di un file si sovrappongono agli intervalli di un altro file?"
- "qual è la copertura di un insieme di regioni?"

Questo la rende molto flessibile per regioni personalizzate, ma meno immediata di [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]] o [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]] quando l'obiettivo è produrre una matrice standard **gene × campioni** per [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]].

## Input e output

Input tipici:
- file **BAM** o **BED** con reads/allineamenti;
- file **BED**, **GTF** o [[GFF - Formato per annotazione genomica|GFF]] con regioni genomiche annotate;
- eventuali file di regioni da includere o escludere, come blacklist, promotori, esoni, finestre genomiche o picchi.

Output possibili:
- conteggio di quante reads/intervalli si sovrappongono a ogni regione;
- numero di basi coperte;
- frazione di regione coperta;
- nuove liste di intervalli ottenute da intersezione, sottrazione, fusione o filtraggio.

Quindi BEDTools non produce necessariamente una matrice di conteggi già pronta: spesso genera risultati intermedi che devono essere aggregati e trasformati con passaggi ulteriori.

## Comandi utili per il conteggio

### `intersect`

`bedtools intersect` identifica sovrapposizioni tra due insiemi di intervalli. Nel conteggio RNA-seq si può usare per contare quante reads cadono dentro regioni annotate.

Esempio:

```bash
bedtools intersect \
  -a genes.bed \
  -b sample.bam \
  -c > gene_counts.bed
```

In questo caso:
- `-a genes.bed` contiene le regioni da contare, ad esempio geni o esoni;
- `-b sample.bam` contiene le reads allineate;
- `-c` aggiunge a ogni regione di `genes.bed` il numero di allineamenti sovrapposti.

Questa operazione è semplice, ma il risultato dipende da come sono state definite le regioni in `genes.bed`. Se gli esoni dello stesso gene sono separati, sovrapposti o condivisi con altri geni, bisogna decidere esplicitamente come aggregarli.

### `coverage`

`bedtools coverage` misura la copertura delle regioni in `-a` rispetto agli intervalli in `-b`.

Esempio:

```bash
bedtools coverage \
  -a exons.bed \
  -b sample.bam > exon_coverage.txt
```

L'output può includere:
- numero di reads che si sovrappongono alla regione;
- numero di basi coperte;
- lunghezza della regione;
- frazione della regione coperta.

Questo è utile quando interessa la **copertura** più che il semplice conteggio di reads, ad esempio per valutare uniformità, regioni non coperte o segnali su finestre genomiche.

### `multicov`

`bedtools multicov` permette di contare reads su un insieme di regioni per più file BAM contemporaneamente.

Esempio:

```bash
bedtools multicov \
  -bams sample1.bam sample2.bam sample3.bam \
  -bed genes.bed > counts_matrix.bed
```

Questo produce una tabella con una riga per regione e una colonna di conteggio per ciascun BAM. È vicino all'idea di matrice regioni × campioni, ma resta responsabilità dell'utente definire correttamente le regioni e le regole di conteggio.

## Come usarlo per RNA-seq

Per usare BEDTools in una quantificazione RNA-seq gene-level bisogna costruire esplicitamente le regioni da contare. Un workflow possibile è:
1. partire da una annotazione GTF/GFF;
2. estrarre gli esoni;
3. raggruppare o fondere gli esoni per gene;
4. gestire sovrapposizioni tra geni diversi;
5. filtrare per strand, se la libreria è stranded;
6. contare le reads o frammenti sovrapposti;
7. aggregare i conteggi in una tabella gene × campioni.

Questi passaggi sono automatici o semi-automatici in [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]] e [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]], mentre in BEDTools devono essere progettati con attenzione. Per questo BEDTools è molto potente, ma più rischioso se usato come contatore RNA-seq standard.

## Parametri e aspetti critici

### Definizione delle regioni

La scelta del file `BED/GTF/GFF` usato come `-a` determina cosa viene contato:
- geni interi;
- esoni;
- promotori;
- finestre genomiche;
- picchi ChIP-seq o ATAC-seq;
- regioni custom.

Per RNA-seq gene-level, contare geni interi può includere introni e regioni non esoniche. Contare esoni separati può invece duplicare o frammentare il segnale se gli esoni vengono poi aggregati male. La costruzione delle regioni è quindi parte essenziale dell'analisi.

### Strand

BEDTools può filtrare le sovrapposizioni in base allo strand:
- `-s`: richiede stesso strand;
- `-S`: richiede strand opposto.

Questa informazione è importante nelle librerie stranded. Se viene ignorata, reads provenienti da trascritti antisenso o geni sovrapposti su strand opposti possono essere contate nella regione sbagliata.

### Overlap minimo

BEDTools permette di controllare quanto overlap deve esserci tra read e regione:
- `-f`: frazione minima della regione `-a` che deve essere coperta;
- `-F`: frazione minima della regione `-b` che deve sovrapporsi;
- `-r`: richiede overlap reciproco;
- `-e`: permette che sia sufficiente una delle due soglie.

Questi parametri sono utili per regioni custom, ma in RNA-seq possono cambiare molto il numero di reads assegnate.

### Paired-end e frammenti

BEDTools lavora principalmente su intervalli. Nei dati paired-end bisogna chiarire se si stanno contando:
- singole reads;
- coppie;
- frammenti ricostruiti dalla coppia.

featureCounts gestisce questo caso in modo più diretto con parametri specifici per paired-end. Con BEDTools può essere necessario preprocessare il BAM o convertire le coppie in intervalli di frammento prima del conteggio.

## Esempio: conteggio su regioni custom

Un caso in cui BEDTools è particolarmente adatto è il conteggio su regioni non standard, ad esempio promotori o finestre genomiche.

```bash
bedtools intersect \
  -a promoters.bed \
  -b sample.bam \
  -s \
  -c > promoter_counts.bed
```

In questo esempio:
- `promoters.bed` contiene regioni promotrici definite dall'utente;
- `sample.bam` contiene reads allineate;
- `-s` richiede coerenza di strand;
- `-c` aggiunge il numero di reads sovrapposte a ciascun promotore.

Questo tipo di analisi è meno naturale con software pensati solo per gene counting, ma è semplice con BEDTools.

## Relazione con featureCounts e HTSeq-count

[[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]], [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]] e BEDTools possono tutti produrre conteggi da allineamenti e annotazioni, ma hanno obiettivi diversi:
- featureCounts è ottimizzato per conteggi RNA-seq gene-level/exon-level su larga scala;
- HTSeq-count privilegia una logica di conteggio esplicita e didattica;
- BEDTools è un toolkit generale per intervalli genomici, utile quando le regioni o le operazioni non rientrano in un workflow RNA-seq standard.

Per una classica differential expression gene-level, featureCounts o HTSeq-count sono in genere più appropriati. BEDTools diventa preferibile quando si lavora con regioni custom, coperture, picchi, finestre o operazioni di overlap non standard.

## Punti di forza

- Molto flessibile: lavora su qualunque regione genomica, non solo geni o esoni.
- Utile anche fuori da RNA-seq, ad esempio in ChIP-seq, ATAC-seq, WGBS e analisi di copertura.
- Componibile: i comandi possono essere concatenati per filtrare, fondere, sottrarre e confrontare regioni.
- Maturo, ampiamente usato e adatto a operazioni di interval logic.
- Buono per analisi esplorative e regioni definite dall'utente.

## Limiti e rischi

- Non è RNA-seq specifico: non conosce automaticamente gene-level counting, isoforme, esoni aggregati o regole di assegnazione biologicamente sensate.
- Richiede più passaggi per replicare ciò che featureCounts o HTSeq-count fanno direttamente.
- La gestione di overlap tra geni, strandedness e paired-end è responsabilità dell'utente.
- Può produrre conteggi non confrontabili con quelli di software RNA-seq specializzati se le regole non sono definite con precisione.
- Per una semplice matrice gene × campioni è spesso meno pratico di featureCounts.

## Quando usarlo

BEDTools è indicato quando servono operazioni generali su intervalli genomici: copertura, overlap, regioni custom, promotori, finestre, picchi o confronti tra set di regioni. Per il conteggio RNA-seq gene-level standard, invece, è di solito preferibile usare [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]] o [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]], perché incorporano direttamente le regole tipiche della quantificazione da annotazioni.
