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
dovuta alla combinazione di variabilità biologica tra replicati ed effetti tecnici globali. Il [[Variabili Aleatorie Notevoli - Poisson|modello di Poisson]] non è quindi sufficiente a descrivere i conteggi. Si adotta la **Negative Binomial** (**NB**), che generalizza la Poisson introducendo un parametro di dispersione:$$\begin{array}{}
Y_{gi}\sim \text{NB}(\lambda_{gi},\theta_g)\\
\mathbb{E}[Y_{gi}] = \lambda_{gi}\\
\mathrm{Var}(Y_{gi}) = \lambda_{gi} + \theta\,\lambda_{gi}^2
\end{array}$$dove $\theta$ è il parametro di **dispersion**: controlla il termine quadratico che permette alla varianza di crescere più rapidamente della media e quindi di modellare la variabilità aggiuntiva osservata tra campioni.
La quantità $\sqrt{\theta}$ è spesso interpretata come **biological coefficient of variation (BCV)**, che quantifica la variabilità relativa tra replicati biologici.
![[IMG - RNA-seq overdispersion.png]]





  

### Dai test alla lista geni: p-value, FDR e controlli di sanità

#### Perché la correzione per test multipli è obbligatoria

Nella **differential expression analysis** si esegue un test statistico per migliaia di geni. Anche senza segnale reale, usando una soglia nominale come 0.05, ci si aspetta quindi un numero non trascurabile di falsi positivi.   

Per questo si usa tipicamente il controllo della **False Discovery Rate (FDR)**, spesso tramite procedura di Benjamini–Hochberg. 

  

#### “Prima della biologia”: controlli pratici che evitano errori grossolani

Prima di interpretare biologicamente la lista di geni è utile controllare alcuni aspetti pratici:
- separare geni up/down con soglie ragionate (es. padj e log2FC),
- controllare artefatti evidenti (geni con conteggi bassissimi ovunque, dominanza di mitocondriali/ribosomiali),
- mappare correttamente gli identificativi (Ensembl ↔ simboli ↔ Entrez) perché molti tool di enrichment richiedono ID specifici. 
Qui lo snodo “ID mapping” è spesso sottovalutato: un mapping scorretto o incompleto altera direttamente le analisi biologiche successive e la narrativa finale.

  

#### Diagnostica visiva come strumento di validazione, non estetica

Alcuni grafici funzionano come strumenti diagnostici:
- **Volcano plot** (effetto vs significatività),   
- **Heatmap** dei top N geni su valori normalizzati/trasformati,   
- **MA plot** (simmetria e dipendenza dall’espressione media): utile per capire se la normalizzazione è ragionevole, e se grandi fold-change provengono soprattutto da geni a bassa espressione (più rumorosi).   

  

Questi grafici non “provano” che l’analisi è corretta, ma aiutano a riconoscere pattern incompatibili con assunzioni del modello o con una normalizzazione adeguata. 

  

## Dalla lista di geni alla biologia: enrichment, GO e limiti interpretativi

Una volta ottenuta una lista (spesso rankata) di geni, l’obiettivo è collegarla a conoscenza biologica esistente tramite **functional enrichment**. Le lezioni definiscono l’enrichment come metodo computazionale per identificare funzioni/pathway sovra-rappresentati, utile per generare ipotesi e riassumere risultati. 

  

### ORA vs GSEA come due famiglie di approcci

Le lezioni distinguono:
- **ORA (Over-Representation Analysis)**: input = lista “significativa”; tipicamente usa test ipergeometrico/Fisher e richiede correzione FDR anche qui.   
- **GSEA / threshold-free**: usa tutti i geni rankati e valuta se un gene set è concentrato in cima o in fondo alla lista; utile quando gli effetti sono diffusi e non vuoi dipendere da un cutoff arbitrario.
GSEA è stata proposta come metodo knowledge-based per interpretare profili genome-wide focalizzandosi su set di geni (pathway/funzioni), aumentando robustezza quando i cambiamenti sono coordinati ma moderati.

  

### Gene Ontology come “linguaggio comune” e struttura a DAG

Le lezioni presentano GO come vocabolario controllato con tre rami (BP/MF/CC) e struttura a **directed acyclic graph (DAG)**, con relazioni parent/child e diversi livelli di specificità.   

Il lavoro fondativo del  descrive GO come vocabolario dinamico per unificare descrizioni funzionali tra organismi.

  

### Scelta del background: dettaglio “semplice” ma decisivo

Le lezioni insistono su un punto spesso trascurato: il *background gene set* deve essere appropriato (idealmente: tutti i geni “catturabili” nel tuo esperimento, non “tutti i geni del genoma” in astratto). Un background sbagliato altera p-value e conclusioni. 

  

### Limiti tipici dell’enrichment

Le lezioni elencano limiti strutturali:
- set piccoli hanno poca potenza,
- test ipergeometrico favorisce set grandi,
- geni multi-funzione generano ridondanza,
- bias di annotazione rende “invisibili” geni poco annotati (spesso non-coding). 
(Software/tool: [[clusterProfiler]], [[g:Profiler]], [[WebGestalt]], [[Enrichr]])

  
