---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi RNA-seq 
---
L’**RNA-seq** è una tecnologia sperimentale per profilare il trascrittoma tramite [[Tecnologie di sequenziamento|sequenziamento ad alta processività]], accompagnata da una pipeline computazionale che trasforma le *reads* in stime quantitative dell’abbondanza di [[RNA]] e in confronti statistici tra condizioni sperimentali. Si distinguono i termini:
- **Campione**: una singola libreria sequenziata; corrisponde a una colonna della matrice dei conteggi.  
- **Condizione**: etichetta sperimentale assegnata a ciascun **campione** che indica a quale gruppo appartiene e quale confronto sperimentale si intende effettuare (es. “controllo”, “trattato”).  
- **Replicati**: più **campioni** associati alla stessa **condizione**; permettono di stimare la variabilità interna al gruppo e distinguere differenze sistematiche da fluttuazioni casuali o tecniche.
L’analisi non riguarda singoli campioni isolati, ma il confronto tra **gruppi di campioni** infatti Il dato prodotto dall’RNA-seq è  una matrice **[[Gene|geni]] × campioni**, ma il significato dell’analisi nasce dall’associazione di ciascun campione a una condizione: è questa struttura a definire quali gruppi vengono confrontati e come interpretare eventuali differenze nei conteggi. 

Gli obiettivi di questa analisi possono essere:
- **Stimare espressione genica**: capire ***quanto*** un gene è espresso in un campione 
- **Identificare nuovi trascritti**: rilevare RNA non presenti nelle annotazioni note. può trattarsi di: nuovi geni, nuove isoforme di geni esistenti, trascritti non codificanti. emerge quando reads si allineano in regioni non annotate o con pattern di splicing inattesi.
- **Rilevare trascritti di fusione**: individuare RNA che derivano da due geni diversi uniti insieme. tipico di: riarrangiamenti genomici, tumori. Si osserva quando una read (o coppia di reads) mappa su due geni distinti.

![video spiegazione](https://www.youtube.com/watch?v=tlf6wYJrwKY)
![altro video](https://www.youtube.com/watch?v=7BLS_YY9HeM)

![altro video](https://www.youtube.com/watch?v=Hv5flUOsE0s)

l'RNA-seq **non osserva direttamente l’espressione**, ma osserva conteggi di reads prodotti dalle [[tecnologie di sequenziamento|tecnologie di sequenziamento]]. Si tratta quindi di un **campionamento rumoroso** con molte sorgenti di variabilità; per questo l’analisi RNA-seq è, in sostanza, un problema di **[[Inferenza statistica|inferenza statistica]] su dati di conteggio**.

Le reads ottenute sono una proiezione parziale del trascrittoma reale: il numero osservato per un gene dipende non solo dall’abbondanza biologica ma anche da molte sorgenti di rumore che si sovrappongono.
**Tipi principali di rumore presenti nei dati RNA-seq:**
- **Variabilità biologica**: differenze reali tra campioni anche nella stessa condizione (fluttuazioni cellulari, stato fisiologico, eterogeneità del tessuto). Questo introduce dispersione reale tra replicati.
- **Rumore di campionamento**: il sequenziamento osserva solo una frazione delle molecole presenti. I trascritti poco espressi vengono campionati raramente e questo porta ad alta variabilità relativa dei conteggi bassi.
- **Rumore tecnico di laboratorio**: estrazione [[RNA|RNA]], preparazione libreria, [[Polymerase chain reaction (PCR)|PCR]], sequenziamento. campioni biologicamente identici possono produrre distribuzioni di reads diverse.
- **Bias di composizione**: pochi geni molto espressi possono occupare gran parte delle reads disponibili, gli altri geni risultano artificialmente meno rappresentati.
- **Bias di lunghezza**: trascritti più lunghi generano più frammenti e quindi più reads. conteggi più alti non implicano necessariamente maggiore espressione.
- **GC bias**: la [[Definizione di Probabilita|probabilità]] di sequenziare una regione dipende dal **contenuto [[Nucleotidi|basi GC]]**, regioni **GC-rich** o **GC-poor** possono essere sovra/sotto-rappresentate questo porta a **distorsione sistematica** nei conteggi.
- **Ambiguità di mapping**: una read può essere compatibile con più isoforme o regioni genomiche porta a incertezza nell’assegnazione delle reads e nei conteggi finali.

Inoltre, “cosa stai misurando” può cambiare:
- **gene-level**: si aggregano più trascritti sotto lo stesso gene, meno ambiguità ma meno risoluzione;
- **transcript-level**: si stimano isoforme singole, maggiore informazione ma più ambiguità di mapping.
Questa scelta influenza reference usata, tipo di quantificazione e aspettative del downstream (conteggi grezzi vs quantità già normalizzate).


un overview del workflow totale è il seguente: ![[IMG - Analisi RNA-seq workflow.png]]
La pipeline RNA-seq può essere vista come una sequenza di trasformazioni che parte da [[RNA|frammenti di RNA]] e arriva a inferenze statistiche sull’espressione, l analisi si divide in fasi e ognuna di queste introduce assunzioni e possibili distorsioni che vanno poi trattate esplicitamente. ogni fase ha molte scelte e software possibili ognuno con i suoi vantaggi e svantaggi. Le fasi posso essere riassunte come: 
1) Si parte dai **dati grezzi di sequenziamento**: reads corte con qualità per base. In questa fase il problema principale è valutare e ripulire il segnale (adattatori, basi a bassa qualità, contaminazioni), perché errori qui si propagano a tutte le fasi successive.
2) Le reads pulite vengono poi **associate a un riferimento** ([[Genoma|genoma]] o trascrittoma). Questo passaggio serve a capire da quale gene o trascritto può provenire ;ogni read. Non è un’operazione perfetta: splicing, regioni ripetute e isoforme multiple introducono ambiguità e incertezza.
3) Una volta stabilite le possibili origini delle reads, si passa alla **quantificazione**: trasformare allineamenti o pseudo-allineamenti in conteggi per gene o per trascritto. Qui si decide cosa si sta misurando (gene-level vs transcript-level) e come gestire reads ambigue o multi-mapping.
4) I conteggi ottenuti non sono ancora confrontabili tra campioni. Serve quindi una **normalizzazione**, che corregga differenze di profondità di sequenziamento, composizione e altri effetti tecnici, in modo che i valori possano essere confrontati tra condizioni.
5) **modello statistico dei conteggi**. Poiché RNA-seq produce dati discreti e rumorosi, si usano modelli di conteggio (tipicamente con dispersione) per separare variabilità biologica da rumore tecnico.
6) **differential expression analysis (DEA)** o **Differential  Expressed Genes Analysis (DEG)**, in cui si testano differenze tra condizioni per ogni gene o trascritto. Il risultato è una lista di elementi con stima dell’effetto e significatività statistica.
7)  **interpretati biologicamente**: si osservano pattern globali, si visualizzano i dati e si collegano i geni differenzialmente espressi a funzioni, pathway o processi biologici.


### Qualità dei reads e trimming
Il dato iniziale è tipicamente un [[Formato FASTQ|file FASTQ]], che contiene sequenze di reads e una stima di qualità per ciascuna base. Questa fase rappresenta il punto più vicino al processo sperimentale e concentra gran parte del rumore tecnico. Prima di qualunque analisi a valle è necessario valutare la qualità dei dati e mitigare errori evidenti, perché qualunque distorsione introdotta qui si propaga nelle fasi successive (mapping, conteggi, modelli statistici).
La fase iniziale di controllo qualità e preprocessing serve a individuare e correggere problemi come:
- **basi a bassa qualità**: aumentano la probabilità di errori di allineamento  
- **adattatori residui**: sequenze tecniche che non rappresentano [[RNA|RNA]] biologico  
- **distribuzioni anomale**: ad esempio contenuto GC distorto  
- **duplicazioni elevate**: possibili artefatti di PCR o profondità non uniforme  
Per mitigare questi problemi si applica il **trimming**, cioè la rimozione con qualità bassa e taglio degli adattatori dai reads. Questo passaggio modifica direttamente la composizione del dataset: cambiano la distribuzione delle lunghezze, il numero di reads e la distribuzione delle qualità. Di conseguenza, influisce sulle statistiche a valle della pipeline e sulle stime di espressione.

per visualizzare la qualità dei i dati si utilizza [[FASTQC - Report di qualità per RNAseq|FASTQC]] 


Strumenti tipici per questa fase: [[Cutadapt - Software di trimming per RNAseq|Cutadapt]], [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]], [[AdapterRemoval v2 - Software di trimming per RNAseq|AdapterRemoval v2]], [[Atropos - Software di trimming per RNAseq|Atropos]], [[fastp - Software di trimming per RNAseq|fastp]].

Una volta ottenuti dati puliti, rimane comunque una fonte importante di variabilità: i **batch effects**. Campioni preparati in momenti, laboratori o condizioni tecniche diverse possono mostrare differenze sistematiche anche in assenza di reali differenze biologiche. Questa variabilità tecnica si sovrappone al segnale biologico e può dominare la struttura dei dati. Se il **batch effect** è forte, i campioni tendono a raggrupparsi per batch invece che per condizione biologica, portando a interpretazioni fuorvianti. Per questo, prima delle analisi inferenziali, si eseguono analisi esplorative come [[Principal Component Analysis (PCA)|PCA]], [[Data analysis -  Clustering|clustering]] gerarchico o **multidimensiona sclaling** (MDS), che proiettano i campioni in uno spazio a bassa dimensione e permettono di visualizzare eventuali raggruppamenti sistematici dovuti a fattori tecnici.
![[IMG - batch effects PCA.png]]
Il grafico mostrato è una **PCA (Principal Component Analysis)**.  
Ogni punto rappresenta un campione RNA-seq; i colori indicano gruppi diversi (ad esempio batch o condizioni).
- **PC1 (67.47%)** e **PC2 (3.42%)** sono le direzioni che spiegano la maggior parte della variabilità nei dati.
- Campioni vicini nel grafico hanno profili di espressione simili.
- Campioni lontani sono più diversi.
In un caso ideale, i campioni dovrebbero raggrupparsi secondo la **condizione biologica**.  
Se invece si raggruppano per colore/batch tecnico, significa che la variabilità tecnica domina quella biologica.
In questo grafico si osservano gruppi separati:  
la componente principale (PC1) spiega gran parte della variabilità, e la separazione tra gruppi suggerisce che esiste una fonte sistematica di differenza tra i campioni. Questa differenza potrebbe essere biologica oppure tecnica; senza ulteriori informazioni, la PCA serve proprio a individuare questo tipo di struttura nei dati.


## Allineamento e ambiguità delle sequenze
Le reads devono essere associate a una possibile origine nel [[Genoma|genoma]] o nel trascrittoma. Questo è un problema di [[Allineamento di sequenze|allineamento di sequenze]] che introduce inevitabilmente ambiguità, perché una read osservata può essere compatibile con più posizioni o più trascritti. Le principali difficoltà sono:
- **Splicing**: reads che attraversano giunzioni tra esoni  
- **Regioni ripetute**: mapping multiplo su più loci  
- **Isoforme diverse**: una read può essere compatibile con più trascritti  
- errori residui di sequenziamento o trimming  
L’allineamento non restituisce una singola assegnazione certa ma un insieme di ipotesi con punteggi di qualità. Le decisioni su come trattare reads ambigue o multi-mapping influenzano direttamente i conteggi e quindi le stime di espressione.

A questo punto si decide **come** associare le reads alla loro origine:
- **[[Allineamento di sequenze pairwise|alignment completo]]**: allineamento base-per-base, spesso verso il genoma, con gestione esplicita delle giunzioni di splicing  
- **pseudoalignment / quasi-mapping**: associazione verso il trascrittoma che stima l’insieme di trascritti compatibili con una read senza costruire un [[Allineamento di sequenze pairwise|allineamento completo]]  

La qualità del reference ([[Genoma|genoma]] o trascrittoma) e delle [[Annotazione genomica|annotazioni genomiche]] è determinante: reference incomplete o annotazioni scarse aumentano l’ambiguità e rendono la quantificazione meno stabile. In assenza di una reference robusta si possono usare approcci alternativi (ad esempio assemblaggio trascrittomico), ma questo sposta l’incertezza sulla ricostruzione delle sequenze e introduce altre fonti di variabilità.

Quando si usa un genoma di riferimento, le annotazioni genomiche permettono di trasformare gli allineamenti delle reads in conteggi per gene, esone o trascritto. In questo senso il genoma fornisce le coordinate, mentre l'annotazione stabilisce quali regioni corrispondono a feature biologicamente interpretabili.

Strumenti tipici:  
- alignment: [[STAR - Software di allineamento per RNAseq|STAR]], [[HISAT2 - Software di allineamento per RNAseq|HISAT2]], [[Bowtie2 - Software di allineamento per RNAseq|Bowtie2]], [[Tophat 2 - Software di allineamento per RNAseq|Tophat 2]]
- pseudoalignment: [[Salmon - Software di allineamento per RNAseq|Salmon]], [[Kallisto - Software di allineamento per RNAseq|Kallisto]]

L’output dell’allineamento contiene tutte le possibili assegnazioni di una read e informazioni associate come posizione, punteggio di allineamento e qualità di mapping (**MAPQ**, Mapping Quality, codificata in scala Phred). I formati più comuni per rappresentare questi risultati sono **SAM** e **BAM**.

Un file **SAM** (Sequence Alignment/Map) è un file di testo tab-delimitato che memorizza reads allineate a un riferimento. È composto da:
- **header**: linee che iniziano con `@`, contenenti metadati su reference, software e gruppi di reads  
- **allineamenti**: ogni riga rappresenta una read e include campi obbligatori come identificatore, riferimento, posizione, qualità e stringa CIGAR  

La **CIGAR string** descrive come la read si allinea al riferimento tramite operazioni (match, inserzioni, delezioni, clipping, ecc.), fornendo una rappresentazione compatta dell’allineamento.

Il formato **BAM** è la versione binaria compressa del SAM. Contiene le stesse informazioni ma in forma più compatta ed efficiente per l’elaborazione computazionale. I file BAM sono normalmente accompagnati da un indice (**BAI**) che permette accesso rapido a regioni specifiche del riferimento.

## Costruzione della matrice di conteggio
Dopo l’allineamento, le reads vengono trasformate in una tabella di conteggi **per gene** o **per trascritto**. Il risultato è una matrice **[[Gene|geni]] × campioni**: ogni cella contiene quante reads sono state assegnate a quella feature in quel campione. Quello che si conta non sono molecole reali ma reads osservate compatibili con una certa regione annotata, quindi una stima indiretta dell’abbondanza.

Operativamente, per ogni read:
- si legge la posizione di allineamento dal file SAM/BAM  
- si verifica con quali feature annotate è compatibile  
- si applicano filtri (qualità di mapping, mapping unico, soglie di overlap)  
- si decide se assegnarla o scartarla  
- se assegnata, si incrementa il conteggio della feature  
Il conteggio non è banale perché una read può trovarsi in casi diversi:
- read completamente dentro un esone  
- read parzialmente sovrapposta a una feature  
- read su giunzione esone-esone  
- read compatibile con più trascritti  
- read che si sovrappone a due geni  
- read con più mapping possibili  
Per questo servono regole di assegnazione:
- **modalità permissiva**: conta se la read tocca la feature  
- **modalità restrittiva**: conta solo se l’assegnazione è univoca  
- regole di overlap (union, intersection-strict, ecc.)  
Regole diverse producono conteggi diversi. Il numero finale per un gene dipende da:
- espressione reale  
- profondità di sequenziamento  
- lunghezza della feature  
- ambiguità di mapping  
- parametri di conteggio  

La matrice di conteggio è quindi una misura proxy dell’abbondanza su cui verranno applicate normalizzazione e modelli statistici.

Strumenti tipici: [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]], [[FeatureCounts - Software di quantificazione per RNAseq|featureCounts]], [[BEDTools - Software di quantificazione per RNAseq|BEDTools]]

![[IMG - matrice conteggi RNAseq.png]]


## Differential expression analysis
La **differential expression analysis** è lo step della pipeline **RNA-seq** in cui si passa dalla matrice di conteggio **geni × campioni** all'identificazione dei geni che cambiano espressione tra condizioni sperimentali. L'obiettivo è valutare, per ciascun gene, se le differenze osservate tra gruppi di campioni sono compatibili con la variabilità attesa dei dati oppure indicano una differenza biologica sistematica.

### Normalizzazione
Nel contesto della **differential expression analysis**, la **normalizzazione** si applica alla matrice dei **conteggi** e serve a rendere comparabili i campioni correggendo differenze tecniche globali, come profondità di sequenziamento, dimensione della libreria e **bias composizionali**. Senza questa correzione, un gene potrebbe apparire più espresso in un campione solo perché quel campione ha un totale di conteggi più alto o perché pochi geni molto espressi occupano una grande frazione della libreria.

Nei dati RNA-seq le principali sorgenti di distorsione da considerare sono:
- **library size**: campioni sequenziati più profondamente producono più reads e quindi conteggi globalmente più alti;
- **library composition**: pochi geni molto espressi possono dominare il totale dei conteggi e alterare la scala apparente degli altri geni;
- **gene length**: geni o trascritti più lunghi tendono a generare più frammenti a parità di abbondanza;
- **GC-content**: regioni con composizione GC estrema possono essere rappresentate in modo non uniforme.

Il **rescaling** porta quindi i campioni su una scala comparabile: un conteggio più alto non viene interpretato automaticamente come maggiore espressione biologica, ma viene valutato tenendo conto della scala complessiva del campione. 

I principali approcci di normalizzazione si possono distinguere in:
- **metodi di scaling tra campioni**: correggono differenze globali di library size o composizione;
- **misure di abbondanza corrette per lunghezza**: utili soprattutto per confronti di abbondanza tra geni o trascritti.

I metodi mostrati nell'immagine sono:
- **RawCount**: conteggi grezzi, non normalizzati. Mostrano la distribuzione originale dei conteggi assegnati ai geni in ciascun campione.
- **Total Count (TC)**: riscalare i conteggi in base al totale dei conteggi del campione, cioè alla somma delle reads assegnate ai geni. Corregge la library size, ma è sensibile a pochi geni estremamente espressi.
- **Upper Quartile (UQ)**: usa il **[[Quantili e Percentili|terzo quartile]]** della distribuzione dei conteggi, cioè il valore sotto cui cade circa il 75% dei geni del campione, invece del totale dei conteggi. Riduce l'effetto dei geni molto espressi rispetto a TC.
- **Median (Med)**: usa la mediana dei conteggi del campione come riferimento di scala. È più robusto del totale perché dipende meno dagli estremi.
- **DESeq (median of ratios)**: calcola, per ogni gene, il rapporto tra il conteggio del campione e la [[Media geometrica]] del gene tra tutti i campioni; il fattore di scala è la mediana di questi rapporti. Assume che la maggior parte dei geni non sia differenzialmente espressa e che gli effetti di sovra- e sotto-espressione siano abbastanza bilanciati.
- **TMM (Trimmed Mean of M-values)**: usato in [[edgeR - DE per RNAseq|edgeR]], confronta ciascun campione con un riferimento e scarta i log-ratio estremi e i geni molto espressi. Serve a correggere **bias composizionali** ed è robusto quando pochi geni ad alto conteggio distorcono la libreria.
- **Q (quantile normalization)**: forza i campioni ad avere la stessa distribuzione globale dei valori. È utile per rendere le distribuzioni molto allineate, ma può essere troppo forte se esistono differenze biologiche globali reali, perché può sovracorreggere i dati.
- **RPKM**: corregge sia per library size sia per lunghezza del gene. È utile per confrontare abbondanze tra geni nello stesso campione, ma non è in genere l'input ideale per i modelli gene-level di differential expression; inoltre non corregge bene i bias composizionali.
Misure simili a **RPKM**, come **FPKM** e **TPM**, correggono anch'esse per la lunghezza del gene o del trascritto. Sono usate soprattutto per confronti di abbondanza, reporting e visualizzazione.

Il confronto sistematico tra questi metodi mostra che **TC** e **RPKM** sono fragili nella differential expression, soprattutto quando le librerie hanno composizione diversa o pochi geni molto espressi dominano i conteggi. **UQ** e **Median** migliorano rispetto al totale grezzo perché riducono l'effetto degli estremi, ma i metodi più robusti nel confronto sono **DESeq** e **TMM**, che mantengono meglio sotto controllo falsi positivi e differenze di composizione tra campioni. Per questo, nei workflow moderni, si preferisce lasciare i conteggi grezzi come input del modello e usare size factors o normalization factors stimati da [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]].

Le immagini illustrano diversi effetti della normalizzazione e il confronto tra metodi:
La prima immagine confronta, tramite [[Statistica Descrittiva - Box-plot|box-plot]], la distribuzione dei valori di espressione nei campioni dopo diversi metodi di normalizzazione:
- asse $x$: metodo di normalizzazione applicato, ad esempio TC, UQ, Med, DESeq, TMM, Q, RPKM o RawCount;
- asse $y$: valori di espressione normalizzati in scala $\log_2$;
- singolo box-plot: un campione;
- valori riassunti dal box-plot: i valori di espressione di tutti i geni in quel campione.

Ogni box-plot mostra quindi la distribuzione globale dei valori dei geni in un campione. Se la normalizzazione è efficace, i box-plot dei diversi campioni risultano più allineati, indicando che le distribuzioni sono più confrontabili.
![[IMG - normalization effect in Analisi RNA-seq.png]]
L'immagine va letta confrontando, per ogni metodo, quanto le distribuzioni dei campioni risultano simili tra loro. Nei **RawCount** le differenze tra box-plot possono riflettere semplicemente library size diverse. Dopo normalizzazione, ci si aspetta che campioni comparabili abbiano mediane e intervalli interquartili più vicini. Tuttavia un allineamento perfetto non è sempre desiderabile: metodi come **Q** possono forzare distribuzioni troppo simili anche quando esistono differenze biologiche reali.

l immagine riassume la variabilità media tra campioni per ciascun metodo. Valori più bassi indicano maggiore stabilità e quindi migliore capacità di ridurre effetti tecnici globali.
![[IMG - average coefficento fo variance Analisi RNA-seq.png]]  
 mostra un valore medio per metodo. Serve quindi per confrontare rapidamente quali normalizzazioni rendono i campioni più stabili.

L'ultima immagine confronta l'effetto dei metodi di normalizzazione sulla comparabilità tra campioni e sul rischio di falsi positivi.
![[IMG - confronto metodi di normalizazione falsi positivi analisi RNA-seq.png]]
Qui il punto non è solo rendere simili le distribuzioni, ma osservare l'effetto downstream sulla **differential expression analysis**. Una normalizzazione debole può lasciare differenze tecniche che vengono interpretate come geni differenzialmente espressi; una normalizzazione troppo aggressiva può invece alterare il segnale reale. Metodi meno robusti come **TC** e **RPKM** possono introdurre risultati spurii quando la composizione delle librerie cambia molto, mentre **DESeq** e **TMM** controllano meglio questi effetti.


### Visualizzazione dei conteggi
Per visualizzare i conteggi o usarli in analisi esplorative, spesso non si lavora direttamente sulla matrice dei conteggi nella sua scala originale. I conteggi **RNA-seq** hanno infatti una distribuzione fortemente asimmetrica: molti geni hanno conteggi molto bassi o nulli, mentre pochi geni presentano conteggi estremamente elevati. Questo produce distribuzioni fortemente **skewed**.

Le trasformazioni per visualizzazione cambiano la scala dei dati per renderli più interpretabili in [[Principal Component Analysis (PCA)|PCA]], clustering e heatmap. L'obiettivo è:
- comprimere i valori estremamente alti;
- ridurre l'asimmetria della distribuzione;
- rendere la varianza meno dipendente dalla media;
- evitare che pochi geni ad alta espressione dominino distanze tra campioni, PCA e clustering.

Nell’immagine ogni pannello mostra l’[[Statistica Descrittiva - Istogrammi|istogramma]] degli stessi conteggi dopo diverse trasformazioni:
- **naive**: sono i conteggi non trasformati. La distribuzione ha una lunga coda destra: molti valori sono bassi o nulli, pochi valori sono molto grandi. È utile come riferimento, ma tende a far dominare i geni più espressi.
- **log**: comprime i valori alti più di quelli bassi. Riduce la coda destra e rende più visibili differenze tra geni con conteggi medio-bassi. Di solito si usa una forma come $\log(x+1)$ per gestire gli zeri.
- **vst (variance stabilizing transformation)**: trasforma i dati cercando di rendere la varianza più simile lungo tutto il range delle medie. Serve soprattutto quando si vuole che geni a bassa e alta espressione contribuiscano in modo più bilanciato a PCA, clustering e distanze.
- **rlog**: è una trasformazione logaritmica regolarizzata, usata in particolare in [[DESeq2 - DE per RNAseq|DESeq2]]. Ha un effetto simile al log, ma stabilizza meglio i geni con conteggi bassi e riduce l'effetto di variazioni rumorose nei geni poco espressi.
- **Box-Cox**: è una famiglia di trasformazioni parametrica: il log è un caso particolare. Sceglie una trasformazione adatta alla forma dei dati per ridurre asimmetria e coda destra.
- **standardized**: centra e riscalano i valori, portandoli a media 0 e varianza 1. Non cambiano solo la forma della distribuzione, ma mettono le variabili sulla stessa scala. Sono utili quando si vuole evitare che geni con valori assoluti più grandi pesino più degli altri.
- **stand. log / stand. vst / stand. Box-Cox**: prima applicano la trasformazione, poi standardizzano. Sono utili per PCA e clustering quando interessa confrontare pattern relativi tra campioni più che grandezze assolute di espressione.

Dopo queste trasformazioni si ottiene tipicamente:
- distribuzione più simmetrica;
- riduzione della coda destra;
- varianza meno dipendente dalla media;
- distanze tra campioni meno dominate da pochi geni ad alta espressione.

Queste trasformazioni sono quindi usate soprattutto per analisi esplorative e diagnostiche. 
![[IMG - Trasformazioni dati RNA-seq.png]]

### Modellazione statistica dei conteggi
I conteggi RNA-seq sono **conteggi discreti non negativi** salvati nella tabella **geni × campioni**. La modellazione statistica descrive come questi conteggi variano tra campioni, tenendo conto della variabilità biologica tra replicati e della variabilità tecnica residua.

Per costruire il modello è importante descrivere la relazione tra **media** e **varianza**. Nei dati RNA-seq, infatti, i geni con conteggi medi più alti tendono anche ad avere varianza più alta.

Nei metodi come [[DESeq2 - DE per RNAseq|DESeq2]] ed [[edgeR - DE per RNAseq|edgeR]], i conteggi grezzi restano in genere l'input del modello; la normalizzazione entra tramite **size factors** o **offset**.

Per ogni gene si calcolano (**pannello A**):
- la **media dei conteggi** tra tutti i campioni (asse $x$)  
- la **varianza dei conteggi** tra gli stessi campioni (asse $y$)
A ogni gene corrisponde quindi un punto $(x,y)$, dove $x$ rappresenta la [[Idd - Media Campionaria|media]] dei conteggi tra i campioni e $y$ la [[Idd - varianza campionaria|varianza]] dei conteggi per quel gene.

In aggiunta, per un gene specifico è possibile visualizzare la distribuzione dei suoi conteggi tra i campioni (**pannello B**). Il pannello B è un [[Statistica Descrittiva - Istogrammi|istogramma]]:
- asse $x$: intervalli di conteggio del gene selezionato
- asse $y$: numero di campioni che ricade in ciascun intervallo

Non viene quindi mostrato un valore separato per ogni campione, ma la distribuzione complessiva dei conteggi di quel gene nei campioni considerati.
![[IMG - RNA-seq data plot.png]]
Una prima modellazione naturale del rapporto **media-varianza** dei conteggi RNA-seq è usare una [[Variabili Aleatorie Notevoli - Poisson|distribuzione di Poisson]]:$$Y_{gi}\sim \text{Poisson}(\lambda_{gi})$$dove $g$ indica il gene, $i$ il campione e $\lambda_{gi}$ il [[Variabili aleatoria - Valore atteso|numero atteso]] di reads per quel gene in quel campione, determinato da livello di espressione, dimensione della libreria e altri fattori globali.
![[IMG - poisson model per RNA-seq.png]]  
Nei dati RNA-seq la **varianza cresce con la media** più rapidamente di quanto previsto dal modello di Poisson: nei grafici media–varianza la nuvola di punti si colloca sistematicamente sopra la relazione varianza = media. In altre parole si osserva **overdispersion**, cioè
$$\mathrm{Var}(Y_{gi}) \gg \mathbb{E}[Y_{gi}],$$
dovuta alla combinazione di variabilità biologica tra replicati ed effetti tecnici globali. Il [[Variabili Aleatorie Notevoli - Poisson|modello di Poisson]] non è quindi sufficiente a descrivere i conteggi. Si adotta la **Negative Binomial** (**NB**), che generalizza la Poisson introducendo un parametro di dispersione:
$$
\begin{array}{}
Y_{gi}\sim \text{NB}(\mu_{gi},\phi_g)\\
\mathbb{E}[Y_{gi}] = \mu_{gi}\\
\mathrm{Var}(Y_{gi}) = \mu_{gi} + \phi_g\mu_{gi}^2
\end{array}
$$
dove $\mu_{gi}$ è il valore atteso dei conteggi per il gene $g$ nel campione $i$, mentre $\phi_g$ è il parametro di **dispersione** del gene: controlla il termine quadratico che permette alla varianza di crescere più rapidamente della media e quindi di modellare la variabilità aggiuntiva osservata tra campioni.
In [[edgeR - DE per RNAseq|edgeR]], la quantità $\sqrt{\phi_g}$ è spesso interpretata come **biological coefficient of variation (BCV)**, cioè una misura della variabilità relativa tra replicati biologici.
![[IMG - RNA-seq overdispersion.png]]


### Dai test alla lista di geni
La **differential expression analysis** (**DEA**) produce, per ogni gene, una stima dell'effetto e una misura di incertezza. Nei workflow basati su [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]], l'effetto è tipicamente espresso come **log2 fold change**:$$\log_2FC_g = \log_2\left(\frac{\text{espressione nella condizione A}}{\text{espressione nella condizione B}}\right)$$Un valore positivo indica maggiore espressione nella condizione al numeratore, un valore negativo indica minore espressione. Il fold change da solo non basta: un effetto grande stimato su conteggi bassi o molto variabili può essere poco affidabile.

Qui il **modello statistico** è il modello di conteggio usato da tool come [[DESeq2 - DE per RNAseq|DESeq2]] e [[edgeR - DE per RNAseq|edgeR]]: un [[Generalized Linear Model (GLM)|GLM]] basato su [[Variabili aleatorie Notevoli - Negative Binomial|Negative Binomial]]. Per ogni gene $g$, il modello descrive i conteggi osservati nei campioni e collega la media attesa $\mu_{gi}$ alle variabili sperimentali:$$\log(\mu_{gi}) = \log(s_i) + \beta_{g,0} + \beta_{g,\text{condizione}}x_i$$dove $s_i$ è il fattore di normalizzazione del campione $i$, $x_i$ indica la condizione sperimentale del campione e $\beta_{g,\text{condizione}}$ misura l'effetto della condizione sull'espressione del gene $g$. Se questo coefficiente è vicino a zero, il gene non mostra una differenza sistematica tra le condizioni; se è molto diverso da zero, il gene potrebbe essere differenzialmente espresso.

Il [[Test Statistici|test statistico]] formalizza questa domanda confrontando due ipotesi:$$
\begin{align}
H_0: \beta_{g,\text{condizione}}  =  0  \\
H_1: \beta_{g,\text{condizione}}  \neq   0
\end{align}
$$$H_0$ dice che la condizione non ha effetto sull'espressione del gene, quindi le differenze osservate nei conteggi sono compatibili con variabilità biologica, rumore tecnico e campionamento. $H_1$ dice invece che l'effetto della condizione è diverso da zero.

Il test non guarda solo quanto è grande l'effetto stimato, ma lo confronta con la sua incertezza. In pratica valuta se $\hat{\beta}_{g,\text{condizione}}$ è grande rispetto all'errore standard stimato dal modello. Un effetto grande ma molto incerto può non essere significativo; un effetto moderato ma stimato con precisione può invece risultare significativo.

Il risultato è un [[Test Statistici - p-value|p-value]]: sotto l'ipotesi nulla, misura quanto sarebbe raro osservare un effetto almeno così estremo. Un p-value piccolo indica che i dati sono poco compatibili con $H_0$, quindi il gene è un candidato **differenzialmente espresso**.

Poiché l'analisi testa migliaia di geni contemporaneamente, non si può interpretare direttamente una soglia nominale come $p < 0.05$. Anche in assenza di veri effetti biologici, su migliaia di test alcuni geni risulterebbero significativi per caso. Per questo si applica una correzione per test multipli, di solito controllando il [[FDR|False Discovery Rate]] tramite [[Test Statistici - Benjamini-Hochberg correction|Benjamini-Hochberg correction]]. Il valore corretto è spesso indicato come **adjusted $p$-value**, **$p_{adj}$** o **$q$-value**.

Un gene viene considerato interessante quando combina:
- **significatività statistica**, ad esempio $p_{adj} < 0.05$;
- **dimensione dell'effetto**, ad esempio $|\log_2FC|$ sufficientemente grande;
- **conteggi sufficienti**, perché geni quasi non espressi producono stime instabili;
- **coerenza biologica**, valutata nel contesto sperimentale e non solo con una soglia automatica.

L'output della **DEA** può essere usato in due modi:
- come **lista non ordinata** di geni significativi, ottenuta applicando soglie su $p_{adj}$ e $\log_2FC$;
- come **lista rankata**, ordinata secondo una [[Statistiche campionarie|statistica]], ad esempio **Wald statistic**, **likelihood ratio statistic**, $\log_2FC$ o $p_{adj}$.

Questa distinzione è importante perché le analisi di enrichment possono richiedere input diversi: i metodi ORA usano tipicamente una lista di geni significativi, mentre GSEA usa una lista completa e ordinata.

#### Controlli visuali di significatività
I grafici diagnostici non dimostrano da soli che l'analisi è corretta, ma aiutano a capire se i risultati sono coerenti con le assunzioni del modello e con il disegno sperimentale.

Il **volcano plot** rappresenta ogni gene come un punto:
- asse $x$: $\log_2FC$, quindi direzione e dimensione dell'effetto;
- asse $y$: $-\log_{10}(p_{adj})$, quindi significatività statistica.
I geni più interessanti tendono a comparire in alto a sinistra o in alto a destra: hanno effetto grande e adjusted p-value basso. I geni vicini al centro hanno effetto piccolo; quelli in basso hanno bassa significatività.
![[IMG - Vulcano plot significance per geni in  RNA-seq.png]]

La **heatmap** dei top $N$ geni serve a visualizzare il comportamento dei geni più rilevanti, ad esempio i più differenzialmente espressi. Usa valori normalizzati o trasformati, come logCPM, VST o rlog, perché i conteggi grezzi non sono direttamente confrontabili tra campioni. Di solito:
- le **righe** rappresentano i geni;
- le **colonne** rappresentano i campioni;
- il **colore** indica il livello relativo di espressione di un gene in un campione.
 
la **heatmap** aiuta anche a controllare se coerente i dati sono coerenti con il disegno sperimentale. Se l'analisi cattura un segnale biologico reale, i campioni della stessa condizione dovrebbero essere simili tra loro e quindi comparire vicini nella heatmap. Per esempio, i controlli dovrebbero raggrupparsi con altri controlli e i trattati con altri trattati.

La struttura ad albero sopra le colonne o accanto alle righe è un **dendrogramma**, cioè il risultato di un clustering gerarchico. Il dendrogramma raggruppa campioni o geni in base alla somiglianza dei loro profili di espressione:
- rami che si uniscono in basso indicano elementi molto simili;
- rami che si uniscono più in alto indicano elementi più diversi;
- il dendrogramma delle colonne mostra quali campioni sono più simili tra loro;
- il dendrogramma delle righe mostra quali geni hanno pattern di espressione simili.

Se i campioni si raggruppano secondo la condizione sperimentale o secondo il fattore biologico atteso, la lista dei geni è più interpretabile. Se invece si raggruppano per batch, laboratorio, data di sequenziamento o altri fattori tecnici, l'interpretazione della lista di geni è fragile: il segnale principale potrebbe dipendere da un effetto tecnico invece che dalla differenza biologica studiata.
![[IMG - significance heatmap per Analisi RNA-seq.png]]


Il **MA plot** confronta effetto e abbondanza media:
- $M$ indica il log-ratio, spesso interpretabile come $\log_2FC$;
- $A$ indica l'abbondanza media del gene.
In un confronto ben normalizzato, la maggior parte dei geni dovrebbe essere centrata intorno a $M \approx 0$. Se la nuvola è spostata verso l'alto o verso il basso, può esserci un problema di normalizzazione, composizione della libreria o effetto globale molto forte. Ai bassi valori di $A$ ci si aspetta più rumore e fold change più instabili; agli alti valori di $A$ le stime dovrebbero essere più stabili.

Pattern curvi, cluster anomali o bande di punti possono indicare artefatti tecnici, bias di GC-content, geni appartenenti a famiglie ripetute o altri effetti sistematici non modellati.
![[IMG - MA plot Analisi RNA-seq.png]]

#### Controlli prima dell'interpretazione biologica

Prima di passare a pathway enrichment o Gene Ontology conviene controllare:
- separazione tra geni up-regolati e down-regolati;
- soglie coerenti su $p_{adj}$ e $\log_2FC$;
- presenza di geni con conteggi bassissimi, mitocondriali, ribosomiali o altri gruppi dominanti;
- qualità del mapping degli identificativi, ad esempio Ensembl, gene symbol, Entrez ID o UniProt;
- coerenza tra design sperimentale, covariate incluse nel modello e confronto biologico interpretato.
Il mapping degli identificativi è un passaggio critico: molti tool di enrichment richiedono ID specifici e un mapping incompleto può far sparire geni dalla lista, alterando direttamente i risultati a valle.

## Pathway enrichment e interpretazione biologica

Una lista di geni differenzialmente espressi è spesso troppo lunga per essere interpretata gene per gene. Il **functional enrichment** o **pathway enrichment** serve a trasformare una lista di geni in un insieme più compatto di funzioni, pathway, processi biologici o annotazioni sovra-rappresentate. In questo senso collega i risultati RNA-seq a conoscenza biologica esterna.

L'enrichment può aiutare a:
- ottenere una sintesi biologica dei risultati;
- generare ipotesi sui processi cellulari coinvolti;
- verificare se l'esperimento recupera segnali biologici attesi;
- confrontare risultati con pathway noti, [[Gene Ontology (GO)|Gene Ontology]], [[Cell pathways|cell pathways]] o database funzionali.
![[IMG - Analisi RNA-seq enrichment.png]]

### ORA: Over-Representation Analysis

La **Over-Representation Analysis (ORA)** parte da una lista di geni selezionati, ad esempio geni con $padj < 0.05$ e $|\log_2FC| > 1$. Per ogni pathway o termine funzionale si chiede se nella lista significativa compaiono più geni associati a quel termine di quanti ci si aspetterebbe per caso.

Il caso tipico si basa su una tabella di contingenza:
- geni nella lista e nel pathway;
- geni nella lista ma non nel pathway;
- geni fuori dalla lista ma nel pathway;
- geni fuori dalla lista e fuori dal pathway.

Il test più comune è il **test ipergeometrico** o il **test esatto di Fisher**. Se il p-value è basso, il pathway è sovra-rappresentato nella lista. Anche qui si corregge per test multipli, perché vengono testati molti pathway o termini GO contemporaneamente.

Il vantaggio di ORA è la semplicità: prende una lista di geni e produce una lista di termini arricchiti. Il limite principale è che dipende da una soglia arbitraria: geni appena sopra o appena sotto il cutoff vengono trattati in modo completamente diverso.

### GSEA: Gene Set Enrichment Analysis
La **Gene Set Enrichment Analysis (GSEA)** evita di scegliere subito una soglia rigida. Invece di usare solo i geni significativi, usa tutti i geni ordinati secondo una statistica, ad esempio:
- Wald statistic;
- likelihood ratio statistic;
- $\log_2FC$;
- signed $-\log_{10}(p)$.

Per ogni gene set o pathway, GSEA valuta se i geni appartenenti a quel set tendono a concentrarsi in cima o in fondo alla lista rankata. Se un pathway contiene molti geni moderatamente up-regolati o down-regolati, GSEA può rilevarlo anche quando pochi geni superano una soglia stringente di significatività individuale.

GSEA è quindi utile quando:
- gli effetti sono diffusi ma moderati;
- si vuole evitare un cutoff arbitrario su $p_{adj}$;
- interessa il comportamento coordinato di un intero pathway più che il singolo gene.

### Gene Ontology e pathway database

[[Gene Ontology (GO)]] è un vocabolario controllato che descrive le funzioni dei geni secondo tre rami:
- **Biological Process (BP)**: processi biologici, come risposta immunitaria o metabolismo;
- **Molecular Function (MF)**: attività molecolari, come binding o attività enzimatica;
- **Cellular Component (CC)**: localizzazione o componente cellulare.

GO ha una struttura a **directed acyclic graph (DAG)**: un termine può avere più parent e più child, con livelli diversi di specificità. Questa struttura produce ridondanza: termini simili o parent-child possono risultare arricchiti insieme.

Oltre a GO, i tool di enrichment usano spesso database di pathway e gene set come KEGG, Reactome, WikiPathways, MSigDB, TRANSFAC, database di target di transcription factor, firme di malattia, perturbazioni farmacologiche e interazioni proteina-proteina.

### Background gene set

La scelta del **background gene set** è decisiva. Il background rappresenta l'insieme dei geni che avrebbero potuto comparire nella lista. Non dovrebbe essere scelto automaticamente come "tutti i geni del genoma" se l'esperimento poteva misurare solo una parte di essi.

Esempi di background possibili:
- tutti i geni con conteggio totale non nullo;
- tutti i geni che passano il filtro indipendente di [[DESeq2 - DE per RNAseq|DESeq2]];
- tutti i geni espressi nel tessuto studiato;
- tutti i geni con annotazione disponibile nel database usato;
- tutti i geni effettivamente testati nella DEA.

Un background troppo ampio o non coerente cambia i p-value e può produrre conclusioni sbagliate. In generale, il background migliore è l'insieme dei geni che potevano essere catturati e testati nel proprio esperimento.

### Limiti dell'enrichment

L'enrichment non dimostra causalità: mostra associazioni statistiche tra una lista di geni e annotazioni note. I principali limiti sono:
- pathway o termini con pochi geni hanno poca potenza statistica;
- il test ipergeometrico tende a favorire gene set grandi;
- geni multi-funzione possono arricchire molti termini parzialmente ridondanti;
- i database sono sbilanciati verso geni ben studiati e ben annotati;
- geni non annotati, inclusi molti RNA non codificanti, diventano invisibili per l'analisi;
- risultati lunghi e ripetitivi richiedono ulteriore sintesi.

Per ridurre ridondanza e rendere i risultati interpretabili si possono usare strumenti di semplificazione o visualizzazione come REVIGO, `clusterProfiler::simplify()`, `simplifyEnrichment`, `rrvgo`, Cytoscape ed EnrichmentMap.

Tool comuni per pathway enrichment e functional enrichment:
- [[clusterProfiler - Tool per pathway enrichment]]
- [[gProfiler - Tool per pathway enrichment]]
- [[WebGestalt - Tool per pathway enrichment]]
- [[Enrichr - Tool per pathway enrichment]]
- [[STRING - Tool per reti PPI ed enrichment]]
- [[REVIGO - Tool per semplificazione GO]]
- [[Cytoscape EnrichmentMap - Tool per visualizzare enrichment]]
