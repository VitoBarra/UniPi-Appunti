---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Salmon - Software di quantificazione per RNAseq
---
**Salmon** è un software usato nello [[Analisi RNA-seq|step 2 della pipeline RNA-seq]], in cui le reads vengono associate a un [[Genoma di riferimento|riferimento trascrittomico]]. È progettato per stimare in modo rapido e accurato l’abbondanza dei trascritti senza richiedere necessariamente un allineamento genomico completo. Usa strategie di **quasi-mapping / pseudoalignment** per supportare direttamente la quantificazione transcript-level.
Salmon lavora su un **trascrittoma di riferimento**: ovvero, identifica l’insieme di trascritti compatibili con quella read e usa un modello probabilistico per stimarne l’abbondanza.

Contesto d’uso:
- Possibile:
  - generare un’assembly trascrittomica (de novo o reference-based) e quantificare su di essa
  - mappare su trascrittoma con aligner tradizionali (es. [[HISAT2 - Software di allineamento per RNAseq|HISAT2]], [[Tophat 2 - Software di allineamento per RNAseq|Tophat 2]])
- Salmon evita il mapping genomico completo utilizzando direttamente un indice del trascrittoma

### Come funziona
- Richiede un insieme di trascritti di riferimento, tipicamente ottenuti da una annotazione come [[Genoma di riferimento|GENCODE]] o [[Genoma di riferimento|Ensembl]]
- Costruisce un indice del trascrittoma
- Per ogni read o coppia di reads identifica rapidamente i trascritti compatibili
- Risolve l’ambiguità tra isoforme tramite un modello probabilistico
- Raffina le abbondanze tramite algoritmi come **[[Expectation Maximization (EM) Method|Expectation-Maximization]]** o **Variational Bayes**

In pratica, Salmon non risponde alla domanda:
- “in quale posizione esatta del genoma cade questa read?”

ma piuttosto alla domanda:
- “da quale trascritto è più plausibile che questa read provenga?”

### Gene, trascritti e origine dell'ambiguità
Come descritto nelle note sul [[Gene|gene]] e sull'[[RNA|RNA]], un gene può produrre più **trascritti** o isoforme tramite splicing alternativo. Le isoforme possono contenere molti degli stessi esoni, ma differire per l'inclusione di alcuni esoni o per le giunzioni esone-esone.

```text
Gene:          [E1]—[E2]—[E3]
Trascritto T1: [E1]—[E2]—[E3]
Trascritto T2: [E1]—————[E3]
```

Una read è molto più corta del trascritto completo. Una read contenuta in `E1` può quindi essere compatibile sia con `T1` sia con `T2`, mentre una read che attraversa la giunzione `E1-E2` supporta `T1` e una read sulla giunzione `E1-E3` supporta `T2`.

Lo splicing e la distinzione tra esoni, introni e RNA maturo sono approfonditi nella nota sull'[[RNA|RNA]]. Per Salmon è rilevante che un indice del trascrittoma contenga le sequenze trascritte mature, comprese le giunzioni esone-esone, e non le regioni introniche del genoma.

### Reads, frammenti e dati paired-end
Nei dati [[Tecnologie di sequenziamento#Single-end e paired-end|paired-end]], `R1` e `R2` sono le due estremità sequenziate dello stesso frammento. Salmon quantifica il contributo dei **frammenti**, non interpreta le due reads come due osservazioni biologiche indipendenti.

La coppia fornisce più informazione di una singola read perché Salmon può considerare insieme:
- compatibilità delle sequenze di entrambe le estremità;
- orientamento della coppia;
- distanza plausibile tra le estremità, legata alla distribuzione delle lunghezze dei frammenti;
- compatibilità con il `libType` dichiarato.

Una singola estremità può essere compatibile con molte isoforme, mentre la combinazione dei due mate può restringere l'insieme dei trascritti plausibili.

### Insiemi di trascritti compatibili e classi di equivalenza
Per ogni frammento Salmon determina un insieme di trascritti compatibili. Frammenti compatibili con lo stesso insieme possono essere riassunti concettualmente in una **classe di equivalenza**.

```text
Frammento A → {T1, T2, T3}
Frammento B → {T1, T2}
Frammento C → {T3}

Classe {T1, T2, T3}: 100 frammenti
Classe {T1, T2}:       40 frammenti
Classe {T3}:            30 frammenti
```

Dire che i trascritti “condividono le stesse reads” significa quindi che quelle reads potrebbero provenire indistinguibilmente da ciascuno dei trascritti della classe. Non significa che Salmon assegni subito ogni read a un unico trascritto.

### Stima probabilistica delle abbondanze
Salmon usa l'evidenza dell'intero campione per ripartire il contributo dei frammenti ambigui. Il procedimento può essere compreso tramite lo schema dell'algoritmo [[Expectation Maximization (EM) Method|Expectation-Maximization]]:

1. assegna abbondanze iniziali ai trascritti;
2. calcola, per ogni frammento ambiguo, quanto è probabile che provenga da ciascun trascritto compatibile;
3. aggiorna le abbondanze usando questi contributi frazionari;
4. ripete i passaggi finché le stime cambiano pochissimo.

Esempio semplificato con due trascritti:

```text
100 frammenti compatibili con T1 e T2
 30 frammenti specifici di T1
 10 frammenti specifici di T2
```

I frammenti specifici suggeriscono che `T1` sia più abbondante di `T2`. Il modello può quindi attribuire, per esempio, circa il 75% del contributo ambiguo a `T1` e il 25% a `T2`:

```text
T1 ≈ 30 + 75 = 105 frammenti stimati
T2 ≈ 10 + 25 =  35 frammenti stimati
```

Questi numeri illustrano il principio, non una regola fissa: nella stima reale Salmon considera anche compatibilità dell'allineamento, lunghezza efficace, modello dei frammenti e bias tecnici. Poiché il contributo di un frammento ambiguo può essere frazionario, i conteggi stimati possono essere numeri decimali.

Se due isoforme hanno sequenze quasi identiche e non esistono reads o giunzioni che le distinguano, il dato non contiene abbastanza informazione per separarle con precisione. Salmon può rappresentare questa incertezza, ma non eliminarla. In questi casi la somma a livello del gene è spesso più stabile della stima delle singole isoforme.

### Lunghezza efficace e TPM
Il bias dovuto alla lunghezza dei trascritti e le principali misure di normalizzazione sono descritti in [[Analisi RNA-seq#Normalizzazione|Analisi RNA-seq]]. Per Salmon, un trascritto lungo offre più posizioni possibili dalle quali può originare un frammento rispetto a un trascritto corto.

La **lunghezza efficace** approssima la parte del trascritto dalla quale possono essere osservati frammenti, tenendo conto anche della distribuzione delle lunghezze dei frammenti. Salmon usa questa quantità nella stima dell'abbondanza.

Il **TPM** (*Transcripts Per Million*) usa questa correzione e riscala le abbondanze affinché la loro somma nel campione sia un milione. Come discusso in [[Analisi RNA-seq#Differential expression analysis|Analisi RNA-seq]], è utile per descrivere l'abbondanza relativa, ma non sostituisce i conteggi richiesti dai modelli di differential expression come [[DESeq2 - DE per RNAseq|DESeq2]].

### Il file `quant.sf`
Per ogni campione Salmon produce normalmente un file `quant.sf` con una riga per trascritto:

```text
Name  Length  EffectiveLength  TPM   NumReads
T1    2000    1800             20.0  120.4
T2    1000     800             10.0   43.6
```

- `Name`: identificativo del trascritto;
- `Length`: lunghezza della sequenza del trascritto;
- `EffectiveLength`: lunghezza corretta in relazione ai frammenti osservabili;
- `TPM`: abbondanza relativa normalizzata;
- `NumReads`: numero stimato di frammenti attribuiti al trascritto, eventualmente decimale.

### Aggregazione da trascritti a geni
La relazione tra geni, trascritti e identificativi dipende dall'[[Annotazione genomica|annotazione genomica]]. Per ottenere valori gene-level serve una tabella `tx2gene` che associ ogni trascritto al gene di origine:

```text
transcript_id  gene_id
T1             G1
T2             G1
T3             G2
```

I valori dei trascritti appartenenti allo stesso gene vengono aggregati. Nel caso più semplice, il conteggio genico è la somma dei conteggi stimati dei suoi trascritti:

$$C_g=\sum_{t\in g}C_t$$

```text
T1 → G1: 120,4 frammenti stimati
T2 → G1:  43,6 frammenti stimati
G1:      164,0 frammenti stimati
```

Il flusso complessivo è quindi:

```text
FASTQ paired-end
    ↓
trascritti compatibili con ciascun frammento
    ↓
stima probabilistica delle abbondanze transcript-level
    ↓
quant.sf per ogni campione
    ↓
mappa trascritto → gene
    ↓
matrice gene × campione
    ↓
differential expression analysis
```

Per la differential expression, strumenti come `tximport` importano le stime di Salmon e possono correggere l'effetto delle variazioni della lunghezza media dei trascritti tra campioni prima di fornire i dati al modello gene-level.

Cosa fa:
- Quantifica l’espressione a livello di trascritto
- Aggregabile a livello genico
- Output:
  - TPM
  - conteggi stimati (estimated counts)
  - lunghezze efficaci
  - bootstrap / [[Gibbs sampling|Gibbs samples]] per stimare l’incertezza

### Bias corretti da Salmon
Salmon incorpora correzioni per diverse fonti di distorsione sistematica:
- **GC bias**
- **bias posizionale**
- **bias di sequenza**
- distribuzione della lunghezza dei frammenti

Queste correzioni migliorano la qualità della quantificazione rispetto a metodi più semplici che si limitano a contare reads assegnate in modo rigido.

Modalità operative:
- Lightweight quasi-mapping mode (direttamente da FASTQ)
- Alignment-based mode (da BAM genomici pre-calcolati)

### LibType e strandedness
Per usare Salmon correttamente bisogna specificare il parametro `libType`, che descrive come l'orientamento delle reads è collegato al trascritto di origine.

In pratica `libType` indica:
- se i dati sono `single-end` o `paired-end`
- se la libreria è `stranded` o `unstranded`
- nel caso paired-end stranded, quale convenzione di orientamento viene usata

Questo è importante perché Salmon usa questa informazione per assegnare correttamente le reads ai trascritti. Se il `libType` è sbagliato, la quantificazione può essere distorta, soprattutto in regioni con geni sovrapposti o trascritti antisenso.

Valori comuni:
- `A`: autodetection
- `U`: unstranded
- `ISR`: paired-end, stranded, reverse
- `ISF`: paired-end, stranded, forward

### Cosa significa reverse-stranded
Una libreria `reverse-stranded` conserva l'informazione di strand, ma secondo una convenzione in cui l'orientamento delle reads corrisponde al trascritto nella modalità detta `reverse`.

Questo non significa che:
- il sequenziamento sia stato fatto “al contrario”
- `R1` sia automaticamente sense e `R2` antisense

Significa invece che:
- l'informazione di strand è preservata
- la relazione tra reads e trascritto dipende dal protocollo di library preparation
- Salmon deve conoscere questa convenzione per quantificare correttamente

Nei protocolli come `TruSeq Stranded Total RNA`, il caso tipico paired-end è `ISR`.


### Significato biologico di forward e reverse
Dal punto di vista biologico, `forward` e `reverse` non indicano due tipi diversi di RNA, ma il modo in cui il protocollo di preparazione della libreria conserva l''informazione di strand del trascritto di origine.

In pratica:
- il trascritto deriva da uno specifico strand del DNA
- la libreria stranded cerca di mantenere questa informazione
- `forward` e `reverse` descrivono come questa relazione viene codificata nelle reads finali

Questo è particolarmente importante quando esistono trascritti sovrapposti su strand opposti, come i trascritti antisenso, perché permette di distinguere meglio da quale trascritto proviene il segnale osservato.

Esempi:
- Se due geni si sovrappongono ma sono trascritti su strand opposti, un dataset stranded permette di separare il segnale dei due geni; in un dataset unstranded parte delle reads risulterebbe ambigua.
- Se un gene coding ha anche un trascritto antisenso nello stesso locus, la strandedness aiuta a capire se l''espressione osservata appartiene al trascritto sense, all''antisenso, o a entrambi.
- In una libreria `reverse-stranded`, la relazione tra reads e trascritto segue la convenzione `reverse`: questo non cambia la biologia del gene, ma cambia il modo in cui il software deve interpretare l''orientamento delle reads per assegnarle correttamente.


### dalla quantificazione a DEA
Per una [[DESeq2 - DE per RNAseq|DEA con DESeq2]] non si usano direttamente i `TPM` come input del test. In un workflow con Salmon si usano tipicamente:
- i file `quant.sf` prodotti da Salmon
- un passaggio di importazione con `tximport`
- aggregazione da trascritto a gene
- costruzione della matrice di conteggi stimati corretti per lunghezza e library size

Quindi Salmon è compatibile con la DEA, ma attraverso un passaggio intermedio esplicito.



