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
**Salmon** è un software usato nello [[Analisi RNA-seq|step 2 della pipeline RNA-seq]], in cui le reads vengono associate a un riferimento trascrittomico. È progettato per stimare in modo rapido e accurato l’abbondanza dei trascritti senza richiedere necessariamente un allineamento genomico completo. Usa strategie di **quasi-mapping / pseudoalignment** per supportare direttamente la quantificazione transcript-level.
Salmon lavora su un **trascrittoma di riferimento**: ovvero, identifica l’insieme di trascritti compatibili con quella read e usa un modello probabilistico per stimarne l’abbondanza.

Contesto d’uso:
- Possibile:
  - generare un’assembly trascrittomica (de novo o reference-based) e quantificare su di essa
  - mappare su trascrittoma con aligner tradizionali (es. [[HISAT2 - Software di allineamento per RNAseq|HISAT2]], [[Tophat 2 - Software di allineamento per RNAseq|Tophat 2]])
- Salmon evita il mapping genomico completo utilizzando direttamente un indice del trascrittoma

### Come funziona
- Richiede un insieme di trascritti di riferimento, tipicamente ottenuti da una annotazione come GENCODE o Ensembl
- Costruisce un indice del trascrittoma
- Per ogni read o coppia di reads identifica rapidamente i trascritti compatibili
- Risolve l’ambiguità tra isoforme tramite un modello probabilistico
- Raffina le abbondanze tramite algoritmi come **[[z|Expectation-Maximization]]** o **Variational Bayes**

In pratica, Salmon non risponde alla domanda:
- “in quale posizione esatta del genoma cade questa read?”

ma piuttosto alla domanda:
- “da quale trascritto è più plausibile che questa read provenga?”

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
- le reads siano di bassa qualità
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
### Uso corretto nella DEA
Per una [[DESeq2 - DE per RNAseq|DEA con DESeq2]] non si usano direttamente i `TPM` come input del test. In un workflow con Salmon si usano tipicamente:
- i file `quant.sf` prodotti da Salmon
- un passaggio di importazione con `tximport`
- aggregazione da trascritto a gene
- costruzione della matrice di conteggi stimati corretti per lunghezza e library size

Quindi Salmon è compatibile con la DEA, ma attraverso un passaggio intermedio esplicito.







