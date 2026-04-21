---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# HTSeq-count - Software di quantificazione per RNAseq
---
**HTSeq-count** è un comando del pacchetto Python **HTSeq** usato nella fase di [[Analisi RNA-seq#Costruzione della matrice di conteggio|costruzione della matrice di conteggio]] della pipeline [[Analisi RNA-seq|RNA-seq]]. Prende in input reads già allineate, in formato **SAM/BAM**, e una annotazione genomica in formato [[GFF - Formato per annotazione genomica|GTF/GFF]], producendo una tabella di **conteggi grezzi** per feature, di solito per gene.

HTSeq-count risponde alla domanda:
- "quante reads allineate possono essere assegnate in modo coerente a ciascun gene o feature annotata?"

Come [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]], non misura direttamente l'espressione reale, ma costruisce una matrice di conteggi osservati. Questa matrice è poi usata da strumenti di differential expression come [[DESeq2 - DE per RNAseq|DESeq2]] ed [[edgeR - DE per RNAseq|edgeR]], che applicano normalizzazione e modelli statistici sui conteggi.

## Input e output

Input principali:
- file **SAM/BAM** con gli allineamenti prodotti da software come [[STAR - Software di allineamento per RNAseq|STAR]], [[HISAT2 - Software di allineamento per RNAseq|HISAT2]] o [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]];
- file **GTF/GFF** con l'annotazione delle feature da contare;
- parametri che specificano tipo di feature, attributo di raggruppamento, strandedness e modalità di conteggio.

Output principale:
- una tabella con una riga per feature e una colonna di conteggi;
- righe speciali finali che riportano reads non assegnate, ambigue, senza feature, con allineamento non unico o di bassa qualità.

Nel caso gene-level tipico:
- `--type=exon` indica che le feature elementari da considerare sono gli esoni;
- `--idattr=gene_id` indica che gli esoni vengono aggregati usando l'identificativo del gene.

## Come funziona

Per ogni read HTSeq-count:
1. legge la posizione dell'allineamento nel file SAM/BAM;
2. identifica le feature annotate che si sovrappongono alla read;
3. applica una modalità di conteggio per decidere se l'overlap è valido;
4. controlla se l'assegnazione è unica o ambigua;
5. incrementa il conteggio della feature assegnata oppure classifica la read tra quelle non contate.

Il comportamento è deliberatamente esplicito e didattico: HTSeq-count rende abbastanza chiaro perché una read viene contata o esclusa. Questo lo rende utile per capire il problema dell'assegnazione delle reads, anche se su dataset grandi è spesso meno efficiente di featureCounts.

## Modalità di conteggio

La caratteristica più importante di HTSeq-count è la possibilità di scegliere diverse regole per gestire le reads che si sovrappongono a più feature. Le modalità principali sono `union`, `intersection-strict` e `intersection-nonempty`.

### Union

`union` è la modalità più usata. Una read viene assegnata a una feature se l'unione delle posizioni coperte dalla read è compatibile con una sola feature. Se la read si sovrappone a più geni, viene classificata come ambigua.

Questa modalità è un compromesso pratico:
- conta molte reads informative;
- evita di assegnare arbitrariamente reads condivise da più geni;
- funziona bene per analisi gene-level standard.

### Intersection-strict

`intersection-strict` è più restrittiva. Considera solo le feature presenti in tutte le posizioni coperte dalla read. Se anche una parte della read cade fuori da una feature, l'assegnazione può essere scartata.

Questo riduce assegnazioni incerte, ma può perdere molte reads, soprattutto in presenza di annotazioni incomplete, reads su bordi esone-introne o allineamenti complessi.

### Intersection-nonempty

`intersection-nonempty` è una via intermedia. Usa l'intersezione delle feature sovrapposte, ma ignora le posizioni in cui nessuna feature è presente. Può recuperare reads che `intersection-strict` scarterebbe, mantenendo comunque una logica più conservativa rispetto a un conteggio puramente permissivo.

## Parametri critici

### Strandedness

Il parametro `--stranded` specifica se la libreria conserva l'informazione di strand:
- `--stranded=no`: libreria unstranded;
- `--stranded=yes`: libreria stranded secondo la convenzione attesa da HTSeq-count;
- `--stranded=reverse`: libreria reverse-stranded.

Questo parametro è cruciale. Se viene impostato in modo errato, reads provenienti da geni sovrapposti su strand opposti possono essere assegnate alla feature sbagliata o scartate. Il problema è analogo al `libType` in [[Salmon - Software di allineamento per RNAseq|Salmon]] e al parametro `-s` in [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]].

### Feature e attributo

I parametri `--type` e `--idattr` determinano cosa viene contato:
- `--type=exon`: usa gli esoni come intervalli annotati;
- `--idattr=gene_id`: raggruppa gli esoni per gene;
- scegliendo attributi diversi si possono ottenere conteggi per trascritto, gene, exon o altre feature annotate.

Se l'attributo scelto non è coerente con il file GTF/GFF, il conteggio può produrre risultati incompleti o inutilizzabili.

### Ordine e formato del BAM

HTSeq-count richiede che l'input sia coerente con il tipo di dati:
- per dati single-end basta leggere ogni allineamento singolarmente;
- per dati paired-end bisogna trattare correttamente le coppie;
- il file può dover essere ordinato per nome della read quando si lavora con paired-end, perché le due reads della coppia devono essere viste insieme.

Questa è una differenza pratica rispetto a featureCounts, che è più orientato a workflow ad alta scala e gestisce molte opzioni paired-end in modo più diretto.

## Esempio di comando

```bash
htseq-count \
  --format=bam \
  --order=pos \
  --stranded=reverse \
  --type=exon \
  --idattr=gene_id \
  --mode=union \
  sample.bam \
  annotation.gtf > sample_counts.txt
```

In questo esempio:
- `--format=bam` indica il formato degli allineamenti;
- `--order=pos` indica che il BAM è ordinato per posizione;
- `--stranded=reverse` specifica una libreria reverse-stranded;
- `--type=exon --idattr=gene_id` conta esoni aggregati per gene;
- `--mode=union` usa la modalità di assegnazione più comune;
- `sample_counts.txt` contiene i conteggi grezzi del campione.

## Relazione con featureCounts

HTSeq-count e [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]] svolgono lo stesso ruolo generale: trasformano allineamenti genomici e annotazioni in conteggi per feature. La differenza principale è pratica e computazionale:
- HTSeq-count è Python-based, più trasparente e utile per didattica o piccoli progetti;
- featureCounts è implementato in C, multithreaded e molto più adatto a dataset grandi o molti campioni;
- HTSeq-count mette in evidenza le modalità concettuali di assegnazione (`union`, `intersection-strict`, `intersection-nonempty`);
- featureCounts è più naturale in pipeline di produzione ad alta scala.

Dal punto di vista del downstream, entrambi producono conteggi grezzi che possono essere usati in [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]], purché tutti i campioni siano processati con gli stessi parametri.

## Punti di forza

- Interfaccia semplice e storicamente molto usata nei tutorial RNA-seq.
- Logica di conteggio trasparente e facile da spiegare.
- Modalità di conteggio esplicite per gestire feature sovrapposte.
- Utile per piccoli progetti, debugging e didattica.
- Può essere usato anche come libreria Python tramite il pacchetto HTSeq.

## Limiti e rischi

- Più lento di featureCounts su dataset grandi, perché Python-based e tradizionalmente single-threaded.
- Poco adatto a coorti numerose o pipeline ad alta produttività.
- Sensibile a strandedness, ordinamento del BAM e coerenza tra BAM e annotazione.
- Le reads ambigue vengono spesso scartate, quindi regioni sovrapposte o multi-mapping possono ridurre i conteggi assegnati.
- Non risolve probabilisticamente l'ambiguità tra isoforme come [[Salmon - Software di allineamento per RNAseq|Salmon]] o [[Kallisto - Software di allineamento per RNAseq|Kallisto]].

## Quando usarlo

HTSeq-count è indicato per progetti RNA-seq piccoli o medi, per lezioni e per casi in cui si vuole una logica di conteggio facilmente interpretabile. Per grandi dataset bulk RNA-seq, molti campioni o workflow di produzione, [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]] è di solito preferibile per velocità e scalabilità.
