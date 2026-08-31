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
  - mappare su trascrittoma con aligner tradizionali (es. [[HISAT2 - Software di allineamento per RNAseq|HISAT2]], [[Tophat2 - Software di allineamento per RNAseq|Tophat 2]])
- Salmon evita il mapping genomico completo utilizzando direttamente un indice del trascrittoma

### Che cos'è e cosa fa il salmon index
L'**salmon index** è una [[Strutture Dati|struttura dati]], costruita **una sola volta** a partire dal [[Genoma di riferimento|riferimento]], che permette a Salmon di cercare rapidamente dove una read potrebbe essere compatibile. Lo stesso indice può poi essere riusato per tutti i campioni che devono essere quantificati rispetto allo **stesso identico riferimento**.

L'input dell'indicizzazione è un file FASTA con le sequenze di riferimento; l'output è una directory, ad esempio `salmon_index/`, da passare poi a `salmon quant -i salmon_index`. Concettualmente, Salmon trasforma le sequenze in molti **k-mer**: tutte le sottosequenze contigue di lunghezza $k$.

```text
Trascritto:       A C U G G A C U A ...
k = 5:            ACUGG  CUGGA  UGGAC  GGACU  GACUA ...
```

Per ciascun k-mer (e per strutture compattate derivate da essi) l'indice conserva informazione sui riferimenti che lo contengono e sulle loro posizioni. Quando arriva una read, Salmon cerca prima i suoi k-mer nell'indice; i match forniscono rapidamente un piccolo insieme di trascritti candidati. Non confronta quindi la read base-per-base contro ogni trascritto del FASTA. Questo è il motivo per cui l'indicizzazione costa tempo e memoria una volta, mentre la quantificazione di molti FASTQ successivi è veloce.

```text
FASTA di riferimento
        ↓  salmon index
indice: k-mer → riferimenti/posizioni compatibili
        ↓  salmon quant (per ciascun campione)
reads → candidati → verifica/score → classi di equivalenza → abbondanze
```

#### Che cosa entra nell'indice: trascritti maturi e decoy
Per RNA-seq standard, il riferimento principale è il **trascrittoma annotato**: un record FASTA per trascritto maturo/isoforma. Le sequenze contengono perciò esoni già concatenati secondo l'annotazione, comprese le giunzioni esone-esone; non sono la sequenza genomica con introni. Gli identificativi nel FASTA devono corrispondere a quelli che saranno usati nella tabella `tx2gene`.

Oggi è raccomandato un indice **decoy-aware**. Al FASTA dei trascritti si aggiungono sequenze genomiche dette *decoy* e i loro nomi sono indicati con `--decoys`. Le decoy non sono trascritti da quantificare: rappresentano sequenze genomiche che possono essere molto simili a un trascritto annotato. Se una read deriva, per esempio, da una regione genomica non annotata, da un pseudogene o da una sequenza ripetuta, potrebbe condividere k-mer con un trascritto e produrre un'associazione spuria. La presenza delle decoy offre a Salmon un'alternativa: se la read spiega meglio una decoy, l'associazione al trascritto viene scartata o penalizzata invece di gonfiarne artificialmente l'abbondanza.

```text
read ── k-mer condivisi ──→ trascritto T1 candidato
                         └→ decoy genomica D1 candidata

se D1 spiega meglio la read → non usare la read come evidenza per T1
```

Le decoy possono essere un insieme mirato di regioni genomiche simili ai trascritti (*partial decoy*) oppure l'intero genoma (*full decoy*). Il full decoy è più completo ma rende l'indice più grande e più esigente in memoria. Le sequenze decoy vanno aggiunte dopo i trascritti nel FASTA e non compaiono come righe di `quant.sf`.

#### k: compromesso tra sensibilità, specificità e dimensione
Il parametro `-k` stabilisce la lunghezza dei k-mer dell'indice (in Salmon classico il valore comune/predefinito è `31`; deve essere dispari e non superiore a 31). Non è la lunghezza della read né la lunghezza minima dell'intero allineamento: è il seme con cui inizia la ricerca dei candidati.

- un `k` più grande rende i semi più specifici e riduce candidati casuali, ma una read corta o con errore/variante può non contenere alcun k-mer esatto utile;
- un `k` più piccolo aumenta la sensibilità, in particolare per reads corte, ma aumenta anche i match ripetitivi, il numero di candidati e potenzialmente il costo computazionale;
- per reads di almeno circa 75 nt, `k=31` è normalmente una scelta ragionevole; per reads più corte può essere opportuno un valore minore, valutando il mapping rate e la qualità del riferimento.

La scelta di `k` appartiene all'indice: cambiare `-k` richiede di ricostruirlo. Per garantire confronti validi, tutti i campioni dello stesso studio devono essere quantificati con lo stesso indice, la stessa versione dell'annotazione e gli stessi parametri rilevanti.

#### Dall'indice alla selective alignment
L'indice genera **candidati**, non prova da solo che una read sia un vero match. Nella modalità moderna predefinita, *selective alignment*, Salmon:

1. trova match esatti massimali tra la read e l'indice;
2. concatena i match coerenti per ottenere posizioni candidate;
3. calcola un rapido punteggio di allineamento banded per ogni candidato;
4. accetta soltanto candidati con un punteggio sufficiente e usa quelli per la quantificazione probabilistica.

Questa verifica evita il limite della pseudoalignment più semplice: condividere alcuni k-mer non basta necessariamente a dimostrare che l'intera read derivi da quel trascritto. La modalità `--sketch` privilegia invece la velocità e usa i hit dei k-mer/classi di equivalenza senza calcolare il punteggio di allineamento per ogni posizionamento; può essere utile quando il throughput è prioritario, ma la selective alignment è in genere preferibile per accuratezza.

#### Comandi esemplificativi e riproducibilità
Esempio concettuale con un riferimento decoy-aware già preparato:

```bash
salmon index \\
  -t gentrome.fa \\
  -d decoys.txt \\
  -i salmon_index \\
  -k 31 \\
  -p 8

salmon quant \\
  -i salmon_index \\
  -l A \\
  -1 sample_R1.fastq.gz -2 sample_R2.fastq.gz \\
  --validateMappings --seqBias --gcBias \\
  -p 8 -o sample_quant
```

`gentrome.fa` contiene i trascritti seguiti dalle decoy; `decoys.txt` elenca i nomi delle sole sequenze decoy. `-l A` attiva l'autodetection del library type. In versioni recenti la selective alignment è la modalità standard; l'opzione `--validateMappings` compare spesso nei workflow e nelle versioni precedenti per richiedere esplicitamente la validazione degli allineamenti. I parametri effettivamente disponibili dipendono dalla versione installata, quindi vanno registrati insieme a: versione di Salmon, fonte e release di genoma/annotazione, FASTA usato, file delle decoy, `k`, checksum dell'indice e comando completo. Se cambia uno di questi elementi, l'indice va ricostruito e i campioni vanno riquantificati in modo coerente.

> **Distinzione importante.** L'indice è specifico del riferimento, non del campione: non va costruito separatamente per ogni FASTQ. Il `libType`, le reads e le correzioni di bias riguardano invece la successiva esecuzione di `salmon quant` per ciascun campione.

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

#### Regione compresa tra R1 e R2
Se il frammento è più lungo della somma delle due read length, la porzione centrale tra `R1` e `R2` non viene letta direttamente da quella coppia:

```text
Trascritto candidato:
──── R1 ────→ ........ regione non letta ........ ←──── R2 ────
```

Salmon non ricostruisce le basi mancanti della regione centrale. Verifica che entrambe le estremità siano compatibili con lo stesso trascritto e che orientamento e distanza siano plausibili rispetto al library type e alla distribuzione delle lunghezze dei frammenti. Altri frammenti, prodotti da molecole dello stesso trascritto e spezzati in posizioni differenti, possono coprire quella regione.

Una regione può comunque rimanere priva di reads, soprattutto per trascritti poco espressi, profondità insufficiente o bias nella preparazione e nel sequenziamento della libreria. Questa lacuna non impedisce necessariamente di stimare l'abbondanza di un trascritto già presente nel riferimento, se esistono abbastanza frammenti compatibili in altre regioni. Riduce però l'informazione disponibile e può impedire di distinguere isoforme che differiscono proprio nella regione non osservata.

```text
T1: [E1]—[E2]—[E3]
T2: [E1]—————[E3]
          ↑
regione discriminante non coperta
```

In questo caso la stima complessiva a livello del gene può essere più stabile della ripartizione tra `T1` e `T2`. La quantificazione su trascrittoma di riferimento richiede evidenza sufficiente per stimare l'abbondanza, non la lettura completa e senza lacune di ogni singola molecola.

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
- mapping-based mode, direttamente da FASTQ: usa l'indice e selective alignment (oppure `--sketch` per la pseudoalignment senza scoring)
- alignment-based mode, da BAM/SAM già allineato **al trascrittoma**; un BAM in coordinate genomiche non è, nella modalità classica, direttamente equivalente e richiede proiezione in coordinate trascrittomiche o la modalità specifica che usa annotazione genomica nelle versioni che la supportano

### LibType e strandedness
Per usare Salmon correttamente bisogna specificare il parametro `libType`, che descrive come l'orientamento delle reads è collegato al trascritto di origine.

In pratica `libType` indica:
- se i dati sono `single-end` o `paired-end`
- se la libreria è `stranded` o `unstranded`
- nel caso paired-end stranded, quale convenzione di orientamento viene usata

Questo è importante perché Salmon usa questa informazione per assegnare correttamente le reads ai trascritti. Se il `libType` è sbagliato, la quantificazione può essere distorta, soprattutto in regioni con geni sovrapposti o trascritti antisenso.

Il codice del library type combina più informazioni. Nei dati paired-end, la prima lettera descrive l'orientamento reciproco dei mate; la parte finale descrive la strandedness:

```text
I / O / M  +  U / SF / SR
orientamento   strandedness
dei mate
```

L'opzione `A` richiede l'**autodetection**: Salmon esamina le reads e inferisce il tipo di libreria più compatibile. Il tipo dedotto deve essere confrontato con il protocollo sperimentale, perché l'inferenza automatica non sostituisce l'informazione sulla preparazione della libreria.

#### Come Salmon riconosce il library type
Il file [[Formato FASTQ|FASTQ]] non contiene un campo che dichiara se la libreria sia stranded, forward o reverse. Contiene le sequenze, i relativi Phred score e gli identificativi che permettono di associare `R1` e `R2`; tutte le sequenze sono rappresentate in direzione 5'→3'. I suffissi `_1` e `_2` identificano i mate, ma da soli non distinguono `ISF`, `ISR` e `IU`.

Il trascrittoma usato come riferimento fornisce invece sequenze con orientamento noto. Durante l'autodetection, Salmon considera un insieme di frammenti e valuta come `R1` e `R2` risultano orientate nelle associazioni compatibili con questi trascritti. In particolare osserva:

- se i mate sono disposti inward, outward oppure nello stesso verso;
- se `R1` segue l'orientamento del trascritto o quello complementare;
- se la relazione osservata è coerente in una frazione dominante dei frammenti.

Esempio semplificato per una coppia inward:

```text
Trascritto: 5' ─────────────────────────→ 3'

ISF:            R1 ─────→      ←───── R2
ISR:            R2 ─────→      ←───── R1
```

Se prevale la prima configurazione, l'evidenza supporta `ISF`; se prevale la seconda, supporta `ISR`. Se entrambe le direzioni sono rappresentate senza una preferenza coerente, l'evidenza può supportare una libreria unstranded come `IU`.

L'informazione sulla strandedness è quindi presente implicitamente nella relazione tra sequenze, mate e trascritti di riferimento, non come etichetta esplicita nel FASTQ:

```text
solo FASTQ                         → strandedness non dichiarata
FASTQ + trascrittoma orientato     → library type inferibile
inferenza + protocollo sperimentale → verifica del risultato
```

Il confronto con il protocollo di preparazione rimane importante. Un risultato inferito coerente con il protocollo rafforza l'interpretazione; una discordanza richiede di controllare ordine dei mate, metadati e preparazione della libreria.

#### Single-end: `U`, `SF` e `SR`
Nei dati single-end non esiste un orientamento reciproco tra mate, quindi il codice descrive soltanto la strandedness:

- `U` — **unstranded**: la direzione della read rispetto al trascritto non viene usata;
- `SF` — **stranded forward**: la read è attesa nello stesso orientamento del trascritto;
- `SR` — **stranded reverse**: la read è attesa nell'orientamento complementare rispetto al trascritto.

Usando come riferimento un trascritto orientato da sinistra verso destra:

```text
Trascritto:  5' ─────────────────→ 3'

SF:               R ─────→
SR:               ←───── R
U:                entrambe le direzioni sono accettate
```

#### Paired-end: inward, outward e matching
Nei dati paired-end, `R1` e `R2` rappresentano le due estremità dello stesso frammento. La prima lettera del library type descrive come sono orientate l'una rispetto all'altra.

**Inward (`I`)**: i mate puntano verso il centro del frammento.

```text
R1 ─────→              ←───── R2
```

È la configurazione tipica di molte librerie paired-end Illumina.

**Outward (`O`)**: i mate puntano verso l'esterno e si allontanano reciprocamente.

```text
R2 ←─────              ─────→ R1
```

Può essere associata a particolari protocolli, come alcune librerie mate-pair.

**Matching (`M`)**: i due mate hanno lo stesso orientamento.

```text
R1 ─────→              R2 ─────→
```

oppure:

```text
←───── R1              ←───── R2
```

Questa disposizione deve essere dichiarata quando deriva dal design della libreria. Se compare in dati attesi come inward può indicare frammenti o associazioni non compatibili con il tipo dichiarato.

#### Unstranded, forward e reverse nei dati paired-end
La parte finale del codice ha questo significato:

- `U` — **unstranded**: non viene richiesta una specifica relazione con il filamento del trascritto;
- `SF` — **stranded forward**: `R1` segue l'orientamento del trascritto e `R2` quello complementare nella configurazione inward;
- `SR` — **stranded reverse**: `R1` segue l'orientamento complementare al trascritto e `R2` quello del trascritto nella configurazione inward.

Esempio con un trascritto orientato da sinistra verso destra:

```text
Trascritto:  5' ─────────────────────────→ 3'

ISF:             R1 ─────→      ←───── R2
ISR:             R2 ─────→      ←───── R1
```

Nel disegno `ISR`, la freccia di `R1` è opposta a quella del trascritto, mentre `R2` segue l'orientamento del trascritto. La lettera `R` indica questa convenzione reverse-stranded; Salmon non modifica fisicamente né inverte i file FASTQ.

#### Combinazioni principali

| Codice | Tipo di dati | Orientamento dei mate | Strandedness |
|---|---|---|---|
| `U` | single-end | non applicabile | unstranded |
| `SF` | single-end | non applicabile | forward |
| `SR` | single-end | non applicabile | reverse |
| `IU` | paired-end | inward | unstranded |
| `ISF` | paired-end | inward | forward |
| `ISR` | paired-end | inward | reverse |
| `OU` | paired-end | outward | unstranded |
| `OSF` | paired-end | outward | forward |
| `OSR` | paired-end | outward | reverse |
| `MU` | paired-end | matching | unstranded |
| `MSF` | paired-end | matching | forward |
| `MSR` | paired-end | matching | reverse |

### Significato biologico della strandedness
`Forward` e `reverse` non descrivono tipi differenti di RNA: descrivono come il protocollo conserva nelle reads l'informazione sul filamento del trascritto originale.

Questa informazione è importante quando due trascritti occupano la stessa regione ma hanno orientamento opposto:

```text
Trascritto A:  ─────────────────→
Trascritto B:  ←─────────────────
```

In una libreria stranded, l'orientamento aiuta Salmon a distinguere il segnale di `A` da quello di `B`. In una libreria unstranded, una read compatibile con entrambe le sequenze può rimanere ambigua. Lo stesso principio è utile per distinguere un trascritto sense da un trascritto antisenso sovrapposto.

### Il caso `ISR` del progetto
Nel progetto Salmon è stato eseguito con `--libType A` e ha inferito `ISR` per tutti gli otto campioni:

- `I`: `R1` e `R2` sono rivolte verso l'interno;
- `S`: la libreria conserva l'informazione di strand;
- `R`: `R1` è orientata in direzione complementare rispetto al trascritto e `R2` nella stessa direzione del trascritto.

Questa inferenza è coerente con la preparazione `TruSeq Stranded Total RNA`. La coerenza tra protocollo e tipo inferito sostiene l'uso di `ISR` durante la quantificazione.


### dalla quantificazione a DEA
Per una [[DESeq2 - DE per RNAseq|DEA con DESeq2]] non si usano direttamente i `TPM` come input del test. In un workflow con Salmon si usano tipicamente:
- i file `quant.sf` prodotti da Salmon
- un passaggio di importazione con `tximport`
- aggregazione da trascritto a gene
- costruzione della matrice di conteggi stimati corretti per lunghezza e library size

Metodologicamente, `tximport` è il ponte tra la quantificazione **transcript-level** prodotta da Salmon e la [[Analisi RNA-seq#Differential expression analysis|DEA]] **gene-level**. Salmon stima abbondanze per trascritto, usando anche la lunghezza efficace e risolvendo probabilisticamente l'ambiguità tra isoforme; [[DESeq2 - DE per RNAseq|DESeq2]] invece lavora su una matrice **gene × campioni** coerente con modelli statistici sui conteggi.

`tximport` importa i file `quant.sf`, usa una tabella `tx2gene` per associare ogni trascritto al gene corrispondente e produce conteggi stimati aggregati a livello genico. Inoltre può tenere conto del fatto che la lunghezza media dei trascritti associati a uno stesso gene può cambiare tra campioni, ad esempio per diverso uso di isoforme. Questo evita di interpretare come variazione di espressione genica una differenza dovuta solo alla composizione isoformica o alla lunghezza efficace.

I problemi principali che `tximport` aiuta a gestire sono:
- **Stime transcript-level non direttamente gene-level**: Salmon quantifica trascritti, mentre molte analisi di [[Analisi RNA-seq#Differential expression analysis|DEA]] testano geni. Sommare semplicemente i trascritti senza una mappa `tx2gene` esplicita può produrre aggregazioni incoerenti o perdere trascritti.
- **Ambiguità tra isoforme**: reads compatibili con più trascritti vengono ripartite probabilisticamente da Salmon. `tximport` conserva questa informazione nei conteggi stimati invece di trasformarla in assegnazioni rigide.
- **Bias di lunghezza efficace**: a parità di espressione, trascritti più lunghi generano più frammenti osservabili. Salmon stima una `EffectiveLength` per ogni trascritto; `tximport` può usare queste lunghezze per costruire conteggi gene-level più coerenti con il modello downstream.
- **Differential transcript usage**: se in un campione un gene esprime soprattutto un'isoforma lunga e in un altro soprattutto un'isoforma corta, la lunghezza media del gene cambia tra campioni. Senza correzione, questa variazione di isoforme può sembrare una variazione di espressione del gene.
- **Uso scorretto dei TPM**: i `TPM` sono utili per descrivere abbondanze relative, ma non sono l'input appropriato per modelli come [[DESeq2 - DE per RNAseq|DESeq2]], che stimano dispersione e test statistici sui conteggi. `tximport` permette di partire dai file di Salmon senza passare direttamente i `TPM` al test.

Esempio concettuale: un gene $G$ ha due isoforme, $T_1$ lunga e $T_2$ corta. Se nella condizione A domina $T_1$ e nella condizione B domina $T_2$, il numero di frammenti osservabili per lo stesso livello molecolare del gene non è identico, perché le isoforme hanno lunghezze efficaci diverse. `tximport` usa le stime di abbondanza, conteggio e lunghezza efficace per ridurre questo artefatto prima della DEA gene-level.

Quindi Salmon è compatibile con la DEA, ma attraverso un passaggio intermedio esplicito: Salmon produce stime transcript-level, `tximport` le importa e le aggrega in una forma adatta a [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]].
