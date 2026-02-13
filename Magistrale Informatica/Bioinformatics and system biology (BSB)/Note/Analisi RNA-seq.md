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
L’**RNA-seq** è un insieme di tecniche computazionali che trasformano frammenti di [[RNA|RNA]] [[Tecnologie di sequenziamento|sequenziati]] (*reads*) in stime quantitative dell’abbondanza di [[RNA|RNA]] e in confronti tra gruppi sperimentali. Si distinguono i termini:
- **Campione**: una singola libreria sequenziata; corrisponde a una colonna della matrice dei conteggi.  
- **Condizione**: etichetta sperimentale assegnata a ciascun **campione** che indica a quale gruppo appartiene e quale confronto sperimentale si intende effettuare (es. “controllo”, “trattato”).  
- **Replicati**: più **campioni** associati alla stessa **condizione**; permettono di stimare la variabilità interna al gruppo e distinguere differenze sistematiche da fluttuazioni casuali o tecniche.
L’analisi non riguarda singoli campioni isolati, ma il confronto tra **gruppi di campioni** infatti Il dato prodotto dall’RNA-seq è  una matrice **geni × campioni**, ma il significato dell’analisi nasce dall’associazione di ciascun campione a una condizione: è questa struttura a definire quali gruppi vengono confrontati e come interpretare eventuali differenze nei conteggi. 

Gli obiettivi di questa analisi possono essere:
- **Stimare espressione genica**: capire ***quanto*** un gene è espresso in un campione 
- **Identificare nuovi trascritti**: rilevare RNA non presenti nelle annotazioni note. può trattarsi di: nuovi geni, nuove isoforme di geni esistenti, trascritti non codificanti. emerge quando reads si allineano in regioni non annotate o con pattern di splicing inattesi.
- **Rilevare trascritti di fusione**: individuare RNA che derivano da due geni diversi uniti insieme. tipico di: riarrangiamenti genomici, tumori. Si osserva quando una read (o coppia di reads) mappa su due geni distinti.

![video spiegazione](https://www.youtube.com/watch?v=tlf6wYJrwKY)
![altro video](https://www.youtube.com/watch?v=7BLS_YY9HeM)


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
2) Le reads pulite vengono poi **associate a un riferimento** (genoma o trascrittoma). Questo passaggio serve a capire da quale gene o trascritto può provenire ;ogni read. Non è un’operazione perfetta: splicing, regioni ripetute e isoforme multiple introducono ambiguità e incertezza.
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
Le reads devono essere associate a una possibile origine nel [[DNA Struttura e funzionalità|genoma]] o nel trascrittoma. Questo è un problema di [[Allineamento di sequenze|allineamento di sequenze]] che introduce inevitabilmente ambiguità, perché una read osservata può essere compatibile con più posizioni o più trascritti. Le principali difficoltà sono:
- **Splicing**: reads che attraversano giunzioni tra esoni  
- **Regioni ripetute**: mapping multiplo su più loci  
- **Isoforme diverse**: una read può essere compatibile con più trascritti  
- errori residui di sequenziamento o trimming  
L’allineamento non restituisce una singola assegnazione certa ma un insieme di ipotesi con punteggi di qualità. Le decisioni su come trattare reads ambigue o multi-mapping influenzano direttamente i conteggi e quindi le stime di espressione.

A questo punto si decide **come** associare le reads alla loro origine:
- **alignment completo**: allineamento base-per-base, spesso verso il genoma, con gestione esplicita delle giunzioni di splicing  
- **pseudoalignment / quasi-mapping**: associazione verso il trascrittoma che stima l’insieme di trascritti compatibili con una read senza costruire un [[Allineamento di sequenze pairwise|allineamento completo]]  

La qualità del reference (genoma o trascrittoma) e delle annotazioni è determinante: reference incomplete o annotazioni scarse aumentano l’ambiguità e rendono la quantificazione meno stabile. In assenza di una reference robusta si possono usare approcci alternativi (ad esempio assemblaggio trascrittomico), ma questo sposta l’incertezza sulla ricostruzione delle sequenze e introduce altre fonti di variabilità.

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
Dopo l’allineamento, le reads vengono trasformate in una tabella di conteggi **per gene** o **per trascritto**. Il risultato è una matrice **geni × campioni**: ogni cella contiene quante reads sono state assegnate a quella feature in quel campione. Quello che si conta non sono molecole reali ma reads osservate compatibili con una certa regione annotata, quindi una stima indiretta dell’abbondanza.

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

Strumenti tipici:   [[Software di conteggi per RNAseq - HTSeq-count|HTSeq-count]], [[Software di conteggi per RNAseq - featureCounts|featureCounts]], [[Software di conteggi per RNAseq - BEDTools|BEDTools]]

![[IMG - matrice conteggi RNAseq.png]]

## Normalizzazione
Lo **step di normalizzazione** in RNA-seq serve a rendere comparabili i campioni correggendo le differenze tecniche globali, così da preservare principalmente quelle biologiche. Il numero di reads osservate per un gene dipende infatti non solo dalla sua reale abbondanza, ma anche da profondità di sequenziamento, dimensione e composizione della libreria e dalla presenza di pochi geni molto espressi che possono occupare una grande frazione delle reads.  

Senza normalizzazione, **campioni** con più **reads totali** o con una distribuzione **fortemente sbilanciata** tra i geni risulterebbero artificialmente diversi, rendendo fuorvianti i confronti di espressione.

La tecniche per fare **normalizazione** possono essere classificate in due class:
- Usando uno **scaling factor**: si applica un fattore con cui riscalare tutti i conteggi del campione per renderli confrontabili con gli altri
- Usando delle [[Statistiche campionarie|statistiche]] dipendenti dai dati: si costruisce un modello statistico che descrive i dati



I metodo basati su **Scaling factor** sono:
- **Total Count (TC)**: ogni gene viene diviso per il numero totale di reads mappate del campione (library size) e riscalato rispetto alla media tra campioni. È semplice ma sensibile alla presenza di pochi geni molto espressi.
- **Upper Quartile (UQ)**: simile a TC ma usa il quartile superiore dei conteggi (escludendo gli zeri) invece del totale. Riduce l’influenza dei geni estremamente espressi.
- **Median (Med)**: usa la mediana dei conteggi (escludendo gli zeri) come base per lo scaling. È più robusto rispetto al totale.
- **DESeq (median of ratios)**: assume che la maggior parte dei geni non sia differenzialmente espressa. Per ogni gene si calcola il rapporto tra il conteggio nel campione e la [[media geometrica|media geometrica]] del gene tra tutti i campioni; il fattore di scala è la mediana di questi rapporti. I geni non-DE dovrebbero avere rapporto ≈1, quindi la mediana fornisce una stima robusta del fattore di correzione.
- **TMM (Trimmed Mean of M-values)**: assume anch’esso che la maggior parte dei geni non cambi. Si sceglie un campione di riferimento e si calcolano i log-ratio tra campioni; i valori estremi vengono scartati (trim) e si calcola una media pesata. Il fattore risultante corregge bias composizionali tra librerie.
- **Quantile normalization (Q)**: forza le distribuzioni dei conteggi a essere identiche tra campioni. Allinea i quantili delle distribuzioni; introdotto per microarray, può essere usato anche su conteggi trasformati.
- **RPKM**: normalizza per dimensione della libreria e lunghezza del gene. È utile per confronti di abbondanza all’interno di un campione, ma nella differential analysis può introdurre bias nelle varianze tra geni, soprattutto per geni poco espressi.
Dopo aver stimato i fattori di normalizzazione, i conteggi grezzi vengono divisi per questi fattori per ottenere conteggi normalizzati tra campioni. L’obiettivo è che differenze residue tra campioni riflettano variazioni sistematiche e non differenze tecniche globali.


Un aspetto pratico è la coerenza tra quantificazione e analisi a valle: alcuni quantificatori transcript-level producono abbondanze già normalizzate (es. TPM) o conteggi stimati. Non sempre questi valori sono adatti direttamente a tutti i modelli di differential expression, quindi il tipo di output deve essere compatibile con il metodo statistico scelto.

Le immagini illustrano diversi effetti della normalizzazione e il confronto tra metodi:

Mostra come la distribuzione dei conteggi tra campioni diventi più uniforme dopo la normalizzazione. Prima della correzione, le distribuzioni possono essere spostate o avere scale diverse; dopo l’applicazione di fattori di scala, le distribuzioni risultano comparabili. ![[IMG - normalization effect in Analisi RNA-seq.png]]

  Confronta il coefficiente di variazione tra campioni per diversi metodi. Metodi di normalizzazione efficaci riducono la variabilità tecnica tra replicati, rendendo più stabile la distribuzione dei conteggi.![[IMG - box conefficient variation analisi RNA-seq.png]] 
  Riassume la variabilità media tra campioni per ciascun metodo. Valori più bassi indicano maggiore stabilità e quindi migliore capacità di ridurre effetti tecnici globali.![[IMG - average coefficento fo variance Analisi RNA-seq.png]]  

  Confronta il tasso di falsi positivi nei test di espressione differenziale. Metodi di normalizzazione meno robusti possono introdurre differenze spurie tra campioni e aumentare i falsi positivi; metodi robusti mantengono il tasso vicino al livello atteso. ![[IMG - confronto metodi di normalizazione falsi positivi analisi RNA-seq.png]]



I metodo basati su un modello statistico sono piu complessi e hanno bisogno di piu informazioni.

I dati RNA-seq sono **conteggi discreti non negativi**. Per esplorare la tabella **geni × campioni** si analizza, per ciascun gene, la relazione tra **media** e **varianza** dei conteggi osservati nei diversi campioni.

Per ogni gene si calcolano (**pannello A**):
- la **media dei conteggi** tra tutti i campioni (asse $x$)  
- la **varianza dei conteggi** tra gli stessi campioni (asse $y$)
A ogni gene corrisponde quindi un punto $(x,y)$, dove $x$ rappresenta la [[Idd - Media Campionaria|media]] del numero di reads tra i campioni e $y$ la [[Idd - varianza campionaria|varianza]] dei conteggi per quel gene.

In aggiunta, per ciascun gene è possibile visualizzare come i conteggi sono distribuiti tra i campioni (**pannello B**), osservando quante reads vengono rilevate in ogni campione e quanto la distribuzione risulti uniforme o concentrata.![[IMG - RNA-seq data plot.png]]
Una prima modellizzazione naturale del rapporto **media-varianza** dei conteggi RNA-seq è usando una [[Variabili Aleatorie Notevoli - Poisson|distribuzione di Poisson]]:$$Y_{gi}\sim \text{Poisson}(\lambda_{gi})$$dove $g$ indica il gene, $i$ il campione e $\lambda_{gi}$ il [[Variabili aleatoria - Momenti|numero atteso]] di reads per quel gene in quel campione, determinato da livello di espressione, dimensione della libreria e altri fattori globali.
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


Un’altra proprietà dei conteggi RNA-seq è la distribuzione fortemente asimmetrica: molti geni hanno conteggi molto bassi o nulli, mentre pochi geni presentano conteggi estremamente elevati. Questo produce distribuzioni fortemente skewed e rende difficile confrontare direttamente livelli di espressione tra geni o campioni. In combinazione con la dipendenza varianza–media, i geni altamente espressi tendono a dominare la variabilità complessiva e le distanze tra campioni.


Per analisi esplorative si applicano trasformazioni ai conteggi della matrice geni × campioni con l’obiettivo di ridurre l’asimmetria, comprimere i valori estremi e rendere la varianza più stabile lungo il range delle medie. Questo permette di ottenere distribuzioni più simmetriche e distanze tra campioni meno dominate da pochi geni molto espressi.
Nell’immagine ogni pannello mostra l’[[Statistica Descrittiva - Istogrammi|istogramma]] degli stessi conteggi dopo diverse trasformazioni:
- **naive**: conteggi grezzi altamente skewed; molti valori piccoli e pochi molto grandi.
- **log**: comprime i valori elevati e riduce l’asimmetria, attenuando la dominanza dei geni molto espressi.
- **vst (variance stabilizing transformation)**: progettata per rendere approssimativamente costante la varianza lungo il range delle medie e produrre una distribuzione più vicina a una gaussiana.
- **rlog**: trasformazione logaritmica regolarizzata che stabilizza soprattutto i geni a bassa espressione.
- **Box-Cox**: famiglia parametrica di trasformazioni (il log è un caso particolare) che riduce l’asimmetria adattandosi ai dati.
- **standardized**: centratura e riscalamento (media 0, varianza 1) applicati ai conteggi o ai conteggi trasformati.
- **stand. log / stand. vst / stand. Box-Cox**: versioni standardizzate dopo trasformazione, utili per PCA e clustering perché mettono tutte le variabili sulla stessa scala.
Dopo trasformazione si ottiene tipicamente:
- distribuzione più simmetrica,
- riduzione della coda destra,
- varianza meno dipendente dalla media,
- distanze tra campioni meno dominate da pochi geni ad alta espressione.
![[IMG - Trasformazioni dati RNA-seq.png]]


gli strumenti comunemente usati sono: [[DESeq2 - DE per RNAseq|DESeq2]] e [[edgeR - DE per RNAseq|edgeR]] 





  

## Dai test alla lista geni: p-value, FDR e controlli di sanità

### Perché la correzione per test multipli è obbligatoria

Le lezioni ricordano che in high-throughput si effettuano migliaia di test; anche senza segnale reale, con soglia 0.05 si ottengono molti falsi positivi attesi.   

Per questo si usa tipicamente il controllo della **False Discovery Rate (FDR)**, spesso tramite procedura di Benjamini–Hochberg. 

  

### “Prima della biologia”: controlli pratici che evitano errori grossolani

Le lezioni suggeriscono una mini-checklist sensata prima di interpretare:
- separare geni up/down con soglie ragionate (es. padj e log2FC),
- controllare artefatti evidenti (geni con conteggi bassissimi ovunque, dominanza di mitocondriali/ribosomiali),
- mappare correttamente gli identificativi (Ensembl ↔ simboli ↔ Entrez) perché molti tool di enrichment richiedono ID specifici. 
Qui lo snodo “ID mapping” è spesso sottovalutato: un mapping scorretto o incompleto altera direttamente l’enrichment e la narrativa biologica finale. Le lezioni citano strumenti e approcci comuni in R e via web. 

  

### Diagnostica visiva come strumento di validazione, non estetica

Le lezioni presentano tre grafici che funzionano come “strumenti diagnostici”:
- **Volcano plot** (effetto vs significatività),   
- **Heatmap** dei top N geni su valori normalizzati/trasformati,   
- **MA plot** (simmetria e dipendenza dall’espressione media): utile per capire se la normalizzazione è ragionevole, e se grandi fold-change provengono soprattutto da geni a bassa espressione (più rumorosi).   

  

Questi grafici non “provano” che l’analisi è corretta, ma aiutano a riconoscere pattern incompatibili con assunzioni del modello o con una normalizzazione adeguata. 

  

## Dalla lista di geni alla biologia: enrichment, GO e limiti interpretativi

Una volta ottenuta una lista (spesso rankata) di geni, l’obiettivo è collegarla a conoscenza biologica esistente tramite **functional enrichment**. Le lezioni definiscono l’enrichment come metodo computazionale per identificare funzioni/pathway sovra-rappresentati, utile per generare ipotesi e riassumere risultati. 

  

### ORA vs GSEA come due famiglie di approcci

Le lezioni distinguono:
- **ORA (Over-Representation Analysis)**: input = lista “significativa”; tipicamente usa test ipergeometrico/Fisher e richiede correzione FDR anche qui.   
- **GSEA / threshold-free**: usa tutti i geni rankati e valuta se un gene set è concentrato in cima o in fondo alla lista; utile quando gli effetti sono diffusi e non vuoi dipendere da un cutoff arbitrario. fileciteturn0file2turn1search3  
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

  