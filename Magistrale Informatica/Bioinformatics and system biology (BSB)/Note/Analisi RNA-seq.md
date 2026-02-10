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
L’analisi RNA-seq è il processo che trasforma reads di RNA sequenziato in stime di espressione genica e in inferenze statistiche sulle differenze tra condizioni biologiche. Non misura direttamente l’espressione: osserva frammenti di RNA campionati in modo rumoroso e cerca di ricostruire le abbondanze originali. L’intero workflow è quindi un problema di inferenza su sequenze e conteggi discreti.

Il contesto biologico è legato alla struttura e funzione dell’[[RNA|RNA]] e ai meccanismi di sequenziamento descritti in [[Tecnologie di sequenziamento|tecnologie di sequenziamento]] e, per la pratica moderna, nel [[Sequenziamento Illumina|sequenziamento Illumina]]. Le reads ottenute sono solo una proiezione parziale del trascrittoma reale: copertura non uniforme, bias di lunghezza, bias di GC e rumore tecnico rendono necessario un trattamento statistico esplicito.

Il dato fondamentale è una collezione di reads con qualità per base. Ogni read è un’osservazione rumorosa di un frammento di RNA. Le difficoltà principali sono:

- errori di sequenziamento  
- presenza di adattatori  
- copertura non uniforme  
- ambiguità di origine  
- bias tecnici tra campioni  

Il trimming e il controllo qualità servono a ridurre errori sistematici che influenzerebbero il mapping e quindi i conteggi finali. Questo passaggio modifica direttamente la distribuzione dei dati e quindi il modello statistico successivo.

## Variabilità tecnica e batch effects
Campioni preparati in momenti o condizioni diverse possono differire sistematicamente anche senza differenze biologiche. Questo introduce variazioni che emergono come cluster artificiali nei dati. L’RNA-seq va quindi interpretato come un problema di separazione tra:

- variabilità biologica reale  
- variabilità tecnica  
- rumore di sequenziamento  

La presenza di batch effects si osserva spesso con analisi esplorative e clustering, collegandosi ai concetti di [[Statistica descrittiva|statistica descrittiva]] e [[Data analysis -  Clustering|clustering]].

![[IMG - batch effects PCA]]

## Allineamento e ambiguità delle sequenze
Le reads devono essere associate a una posizione genomica o trascrittomica. Questo è un problema di [[Allineamento di sequenze|allineamento di sequenze]] con complicazioni specifiche:

- splicing → reads che attraversano giunzioni  
- regioni ripetute → mapping multiplo  
- isoforme diverse → origine ambigua  
- errori residui  

L’allineamento non restituisce una verità certa ma un insieme di ipotesi con punteggi di qualità. La gestione dei mapping multipli e delle reads su giunzioni influisce direttamente sui conteggi finali.

![[IMG - mapping reads splicing]]

## Costruzione della matrice di conteggio
Dopo l’allineamento, le reads vengono trasformate in conteggi per gene o trascritto. Questa trasformazione è tutt’altro che neutra. Occorre decidere:

- come trattare reads che mappano su più geni  
- come trattare reads parziali  
- come gestire giunzioni esoniche  
- soglie di qualità  

Il risultato è una matrice geni × campioni che rappresenta il punto di partenza per l’analisi statistica.

![[IMG - matrice conteggi RNAseq]]

## Problema della normalizzazione
Conteggi più alti non implicano maggiore espressione. Dipendono anche da:

- profondità di sequenziamento  
- composizione del campione  
- geni molto espressi che dominano la libreria  

La normalizzazione mira a rendere comparabili i campioni rimuovendo effetti non biologici. È una fase critica perché influenza direttamente i risultati dei test statistici.

![[IMG - normalizzazione boxplot]]

## Modello statistico dei conteggi
I conteggi RNA-seq sono variabili discrete non negative. Un modello naturale è Poisson:

$$Y_{gi}\sim Poisson(\lambda_{gi})$$

ma nei dati reali la varianza supera la media. Questo fenomeno di overdispersion deriva da variabilità biologica e tecnica. Per questo si usa un modello Negative Binomial:

$$Var(Y)=\mu+\theta\mu^2$$

che introduce un parametro di dispersione. Questo collega l’RNA-seq a concetti di:

- [[Distribuzione di probabilita|distribuzioni]]
- [[Variabili Aleatorie Notevoli - Poisson|Poisson]]
- [[Stima parametrica - Binomiale|stima parametrica]]
- [[Modelli Probabilistici|modelli probabilistici]]

![[IMG - overdispersion RNAseq]]
![[IMG - negative binomial RNAseq]]

## Stabilizzazione della varianza
I dati RNA-seq hanno varianza dipendente dalla media. Per visualizzazioni e clustering si applicano trasformazioni che stabilizzano la varianza. Questo rende confrontabili geni con livelli di espressione diversi e permette analisi geometriche nello spazio dei campioni.

![[IMG - trasformazione varianza RNAseq]]

## Stima della dispersione
Con pochi replicati, stimare la dispersione per ogni gene è instabile. Si usa quindi shrinkage statistico che combina informazione globale e gene-specifica. Questo migliora stabilità e controllo dei falsi positivi, collegandosi ai concetti di inferenza bayesiana e [[Formula di Bayes|Bayes]].

![[IMG - dispersion shrinkage]]

## Test di espressione differenziale
Per ogni gene si testa l’ipotesi di uguale espressione tra condizioni. Poiché si eseguono migliaia di test, è necessario controllare il tasso di falsi positivi. L’analisi si collega a:

- [[Test Statistici|test statistici]]
- [[Probabilita condizionata|probabilità condizionata]]
- [[Inferenza statistica|inferenza statistica]]

Il risultato è una lista di geni con:
- fold change  
- p-value  
- p-value aggiustato  

## Visualizzazione e diagnostica
Grafici principali:

volcano plot  
![[IMG - volcano plot RNAseq]]

heatmap  
![[IMG - heatmap RNAseq]]

MA plot  
![[IMG - MA plot RNAseq]]

Servono a identificare:
- outlier  
- problemi di normalizzazione  
- pattern globali  

## Interpretazione biologica
La lista finale di geni viene collegata a funzioni biologiche tramite database e annotazioni. Questo passaggio non è puramente statistico ma interpretativo e dipende dalla qualità delle annotazioni disponibili.

![[IMG - gene ontology DAG]]

## Struttura concettuale
L’analisi RNA-seq è l’intersezione tra:

biologia molecolare  
statistica dei conteggi  
teoria dell’inferenza  
algoritmi su sequenze  
data analysis ad alta dimensionalità  

Non esiste un singolo punto critico: ogni fase introduce assunzioni che si propagano alle successive. L’interpretazione finale deve sempre considerare l’intera pipeline.






# Approfondimento essenziale su RNA-seq per analisi di espressione

  

## Che cosa misura davvero RNA-seq e quali sono gli obiettivi tipici

L’RNA-seq è un insieme di tecniche sperimentali e passaggi computazionali che trasformano frammenti di RNA sequenziati (“reads”) in stime quantitative dell’abbondanza di RNA e in confronti tra condizioni (per esempio controllo vs trattato). Gli obiettivi più comuni includono: stimare **espressione genica**, identificare **nuovi trascritti**, e rilevare **trascritti di fusione**. fileciteturn0file0

  

Il punto concettuale centrale è che RNA-seq **non osserva direttamente “l’espressione”**, ma osserva conteggi di reads prodotti da (i) campionamento molecolare, (ii) preparazione di libreria e PCR, (iii) sequenziamento e (iv) mappaggio computazionale. Per questo l’analisi RNA-seq è, in sostanza, un problema di **inferenza statistica su dati di conteggio** con molte sorgenti di variabilità. fileciteturn0file1

  

Inoltre, “cosa stai misurando” può cambiare:

- **gene-level** (sommando più trascritti/isoforme sotto lo stesso gene) oppure

- **transcript-level** (isoforme), che espone più ambiguità perché molte reads sono compatibili con più isoforme. fileciteturn0file0

  

Questa scelta influenza quasi tutto il resto: reference usata, tipo di quantificazione, e aspettative del downstream (conteggi grezzi vs quantità già normalizzate). fileciteturn0file0turn0search2turn0search3

  

## Pipeline concettuale: dal FASTQ a una matrice di conteggi

Le lezioni sintetizzano una pipeline “classica” con snodi decisionali importanti (trimming → alignment/pseudoalignment → quantificazione → differential expression). Un messaggio forte è che la pipeline adottata può cambiare in modo significativo l’output (ad esempio la lista di geni differenzialmente espressi), e che non esiste uno strumento “migliore in assoluto”: contano **numero di replicati** e **eterogeneità dei campioni**. fileciteturn0file0turn2search1

  

### Qualità dei reads e trimming

Il dato iniziale è tipicamente un file FASTQ con sequenze e qualità per base. La fase iniziale serve a individuare e mitigare problemi come:

- basi a bassa qualità (più errori di mappaggio),

- presenza di adattatori (reads che non rappresentano RNA biologico),

- distribuzioni anomale (es. contenuto GC distorto), duplicazioni elevate e altri indicatori di artefatti. fileciteturn0file0turn2search1

  

A livello logico, il trimming è “una correzione del segnale in ingresso”: migliora spesso il mappaggio, ma può anche cambiare la composizione del dataset e quindi impattare le statistiche a valle. fileciteturn0file0turn2search1

  

(Software: [[FASTQC]], [[Cutadapt]], [[Trimmomatic]], [[fastp]].) fileciteturn0file0

  

### Batch effects come problema di disegno sperimentale “nascosto”

Le lezioni evidenziano che, oltre alla qualità dei reads, un rischio concreto è la presenza di **batch effects**: differenze sistematiche non previste dal disegno sperimentale (giorno di preparazione, lotto reagenti, lane, operatore). Questi effetti possono dominare le variazioni biologiche e portare a cluster separati “per batch” (spesso visibili con PCA/MDS). fileciteturn0file0

  

In generale, la migliore difesa rimane **prevenzione e tracciamento** (metadata accurati + randomizzazione). Le correzioni post-hoc esistono ma vanno applicate con attenzione, perché possono anche rimuovere segnale biologico se batch e condizione sono confusi (collineari). fileciteturn0file0

  

### Alignment, pseudoalignment e dipendenza da reference/annotazioni

Il passo successivo è decidere *come* associare reads a una origine:

- alignment “completo” (tipicamente verso genoma, gestendo giunzioni di splicing),

- pseudoalignment/quasi-mapping (tipicamente verso trascrittoma), che stima compatibilità read→insieme di trascritti senza allineare base-per-base. fileciteturn0file0turn0search2turn0search3

  

La qualità del reference (genoma/trascrittoma) e delle annotazioni conta molto: reference incompleta o annotazioni scarse aumentano l’ambiguità e rendono meno stabile la quantificazione. Le lezioni indicano anche che, in assenza di reference robusta, si può ricorrere a strategie alternative (es. assemblaggio trascrittomico), ma questo sposta il problema (più incertezza strutturale). fileciteturn0file0

  

(Software: [[STAR]], [[HISAT2]], [[Bowtie2]]; pseudoalignment: [[Salmon]], [[Kallisto]].) fileciteturn0file0

  

### Dall’allineamento al conteggio

L’output dell’allineamento (SAM/BAM) contiene informazioni cruciali: posizione, operazioni di allineamento (CIGAR) e una qualità di mapping (MAPQ). Questi segnali servono a filtrare reads poco affidabili o multi-mappate, e influenzano quindi i conteggi. fileciteturn0file0

  

Il conteggio non è banale perché una read può:

- sovrapporsi parzialmente a un gene,

- attraversare giunzioni esone-esone,

- sovrapporsi a due geni o a regioni condivise.  

Le lezioni mostrano che le regole di assegnazione (union, intersection-strict, ecc.) portano a conteggi diversi. fileciteturn0file0

  

(Software: [[HTSeq-count]], [[featureCounts]], [[BEDTools]].) fileciteturn0file0

  

## Quantificazione e normalizzazione: rendere comparabili campioni diversi

### Counts, TPM e “che cosa entra” nel modello di DE

Un punto operativo sottolineato nelle lezioni: alcuni metodi di quantificazione (soprattutto transcript-level con pseudoalignment) producono in output **quantità normalizzate** (es. TPM) e/o “counts stimati”, e non sempre conteggi grezzi direttamente confrontabili come input per ogni framework di DE. Di conseguenza, la scelta del metodo di DE deve essere coerente con il tipo di dato prodotto. fileciteturn0file0turn0search2turn0search3

  

In letteratura, Salmon viene descritto come quantificatore veloce con modelli di correzione per bias (incluso GC bias a livello di frammento), con l’obiettivo di migliorare accuratezza e sensibilità a valle. citeturn0search2turn0search10  

Kallisto viene descritto come basato su pseudoalignment e stima probabilistica di abbondanze, puntando a eliminare un collo di bottiglia computazionale. citeturn0search3turn0search7

  

### Perché normalizzare: library size e compositional bias

La normalizzazione serve perché “più reads” non significa “più espressione”: dipende anche dalla dimensione della libreria e dalla composizione complessiva dell’RNA del campione. fileciteturn0file1

  

Le lezioni riassumono i *scaling factors* come forma semplice di normalizzazione “between-samples”: ogni campione viene scalato da un fattore (stimato in vari modi) per rendere comparabili i conteggi. Tra i metodi discussi: Total Count, Upper Quartile, Median, DESeq (median of ratios), e TMM. fileciteturn0file1

  

Due idee chiave ricorrono e sono utili da ricordare:

- metodi come DESeq e TMM assumono che **la maggior parte dei geni non sia differenzialmente espressa**, così da stimare un fattore di scala “robusto”; fileciteturn0file1  

- TMM nasce esplicitamente per gestire bias composizionali tramite una media “trimmata” dei log-ratio, ed è proposta come normalizzazione robusta per analisi di DE su RNA-seq. citeturn2search2turn2search6

  

Le slide citano una valutazione comparativa di metodi di normalizzazione su dati reali e simulati, con raccomandazioni pratiche; in quel confronto emergono spesso come scelte robuste DESeq-like e TMM. fileciteturn0file1turn1search0turn1search4

  

### Nota su RPKM/TPM: utili, ma facili da usare male

Le lezioni ricordano che RPKM corregge per library size e lunghezza genica, ma che “correggere per lunghezza” in analisi differenziale può introdurre bias nelle varianze gene-specifiche, soprattutto per geni poco espressi. fileciteturn0file1

  

In letteratura, è stato anche discusso che RPKM può essere “inconsistente” tra campioni e che TPM risolve un problema di interpretazione/scala rispetto a RPKM. citeturn2search3  

Più recentemente, è stato ribadito che TPM/RPKM non rendono automaticamente i campioni confrontabili in senso “assoluto”, perché restano misure relative alla composizione del campione. citeturn2search23

  

Quindi (heuristica utile): TPM/RPKM possono essere ottimi per alcune visualizzazioni e confronti entro-campione, ma per **DE classica** è spesso più sicuro lavorare in framework costruiti per counts con normalizzazione robusta e modello NB, oppure usare approcci specifici per quantificazioni transcript-level. fileciteturn0file0turn0file1turn0search0turn0search1

  

## Modello statistico: perché Poisson non basta e perché si usa la Negative Binomial

Le lezioni sottolineano due proprietà empiriche dei dati RNA-seq:

- i conteggi sono **non negativi** e molto asimmetrici,

- la varianza cresce con la media (mean–variance dependence). fileciteturn0file1

  

### Poisson come punto di partenza

Poisson è un modello intuitivo per conteggi (eventi in un intervallo), con media uguale alla varianza. Le slide lo presentano come idea iniziale: \(Y_{gi}\sim \text{Poisson}(\lambda_{gi})\) e \(\mathbb{E}[Y_{gi}]=\text{Var}(Y_{gi})\). fileciteturn0file1

  

### Overdispersion e Negative Binomial

Nella pratica, però, RNA-seq mostra quasi sempre **overdispersion**: \(\text{Var}(Y)\gg\mathbb{E}(Y)\), dovuta a variabilità biologica tra replicati e variabilità tecnica (prep, sequenziamento). fileciteturn0file1

  

Per questo i metodi moderni per DE usano comunemente la **Negative Binomial**, che generalizza Poisson introducendo una dispersione, in forme del tipo:

\[

\text{Var}(Y_{gi}) = \mu_{gi} + \theta_g \mu_{gi}^2

\]

come riportato nelle lezioni. fileciteturn0file1  

DESeq (storico) e DESeq2 si basano su NB con stima della dispersione per gene e legame varianza–media, e sono presentati come metodi per gestire correttamente variabilità e potenza del test. citeturn2search4turn0search0turn0search4  

Anche edgeR è progettato per conteggi replicati con modello NB e stima empirico-bayesiana dei parametri. citeturn0search1turn0search17

  

### Stabilità con pochi replicati: shrinkage della dispersione

Con pochi campioni per condizione e migliaia di geni, stimare una dispersione indipendente per gene è instabile (soprattutto per geni poco espressi). Le slide descrivono l’approccio di DESeq2: stimare un trend globale dispersione-vs-media e “shrinkare” le stime gene-wise verso il trend (trade-off bias-varianza) per ottenere p-value più calibrati e maggiore potenza. fileciteturn0file1turn0search0  

Un’idea analoga (shrinkage empirico-bayesiano verso common/trended dispersion) è descritta anche per edgeR. fileciteturn0file1turn0search1

  

## Dai test alla lista geni: p-value, FDR e controlli di sanità

### Perché la correzione per test multipli è obbligatoria

Le lezioni ricordano che in high-throughput si effettuano migliaia di test; anche senza segnale reale, con soglia 0.05 si ottengono molti falsi positivi attesi. fileciteturn0file1  

Per questo si usa tipicamente il controllo della **False Discovery Rate (FDR)**, spesso tramite procedura di Benjamini–Hochberg. fileciteturn0file1turn1search1turn1search13

  

### “Prima della biologia”: controlli pratici che evitano errori grossolani

Le lezioni suggeriscono una mini-checklist sensata prima di interpretare:

- separare geni up/down con soglie ragionate (es. padj e log2FC),

- controllare artefatti evidenti (geni con conteggi bassissimi ovunque, dominanza di mitocondriali/ribosomiali),

- mappare correttamente gli identificativi (Ensembl ↔ simboli ↔ Entrez) perché molti tool di enrichment richiedono ID specifici. fileciteturn0file2

  

Qui lo snodo “ID mapping” è spesso sottovalutato: un mapping scorretto o incompleto altera direttamente l’enrichment e la narrativa biologica finale. Le lezioni citano strumenti e approcci comuni in R e via web. fileciteturn0file2

  

### Diagnostica visiva come strumento di validazione, non estetica

Le lezioni presentano tre grafici che funzionano come “strumenti diagnostici”:

- **Volcano plot** (effetto vs significatività), fileciteturn0file2  

- **Heatmap** dei top N geni su valori normalizzati/trasformati, fileciteturn0file2  

- **MA plot** (simmetria e dipendenza dall’espressione media): utile per capire se la normalizzazione è ragionevole, e se grandi fold-change provengono soprattutto da geni a bassa espressione (più rumorosi). fileciteturn0file2  

  

Questi grafici non “provano” che l’analisi è corretta, ma aiutano a riconoscere pattern incompatibili con assunzioni del modello o con una normalizzazione adeguata. fileciteturn0file2

  

## Dalla lista di geni alla biologia: enrichment, GO e limiti interpretativi

Una volta ottenuta una lista (spesso rankata) di geni, l’obiettivo è collegarla a conoscenza biologica esistente tramite **functional enrichment**. Le lezioni definiscono l’enrichment come metodo computazionale per identificare funzioni/pathway sovra-rappresentati, utile per generare ipotesi e riassumere risultati. fileciteturn0file2

  

### ORA vs GSEA come due famiglie di approcci

Le lezioni distinguono:

- **ORA (Over-Representation Analysis)**: input = lista “significativa”; tipicamente usa test ipergeometrico/Fisher e richiede correzione FDR anche qui. fileciteturn0file2  

- **GSEA / threshold-free**: usa tutti i geni rankati e valuta se un gene set è concentrato in cima o in fondo alla lista; utile quando gli effetti sono diffusi e non vuoi dipendere da un cutoff arbitrario. fileciteturn0file2turn1search3  

  

GSEA è stata proposta come metodo knowledge-based per interpretare profili genome-wide focalizzandosi su set di geni (pathway/funzioni), aumentando robustezza quando i cambiamenti sono coordinati ma moderati. citeturn1search3turn1search7

  

### Gene Ontology come “linguaggio comune” e struttura a DAG

Le lezioni presentano GO come vocabolario controllato con tre rami (BP/MF/CC) e struttura a **directed acyclic graph (DAG)**, con relazioni parent/child e diversi livelli di specificità. fileciteturn0file2  

Il lavoro fondativo del entity["organization","Gene Ontology Consortium","ontology consortium"] descrive GO come vocabolario dinamico per unificare descrizioni funzionali tra organismi. citeturn1search2turn1search6

  

### Scelta del background: dettaglio “semplice” ma decisivo

Le lezioni insistono su un punto spesso trascurato: il *background gene set* deve essere appropriato (idealmente: tutti i geni “catturabili” nel tuo esperimento, non “tutti i geni del genoma” in astratto). Un background sbagliato altera p-value e conclusioni. fileciteturn0file2

  

### Limiti tipici dell’enrichment

Le lezioni elencano limiti strutturali:

- set piccoli hanno poca potenza,

- test ipergeometrico favorisce set grandi,

- geni multi-funzione generano ridondanza,

- bias di annotazione rende “invisibili” geni poco annotati (spesso non-coding). fileciteturn0file2

  

(Software/tool: [[clusterProfiler]], [[g:Profiler]], [[WebGestalt]], [[Enrichr]], entity["organization","KEGG","pathway database"], entity["organization","Reactome","pathway database"], entity["organization","WikiPathways","pathway database"].) fileciteturn0file2

  