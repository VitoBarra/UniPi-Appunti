---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi del RNA
---
L’analisi RNA-seq richiede una pipeline articolata perché i dati grezzi ottenuti dal sequenziamento non sono immediatamente interpretabili in termini biologici. L’obiettivo principale è quantificare l’espressione genica, identificare nuovi trascritti o rilevare eventi di fusione, ma ogni risultato dipende in modo critico dalle scelte metodologiche adottate, poiché non esiste uno strumento universalmente ottimale.

Il problema generale consiste nel trasformare reads grezzi in una misura affidabile di espressione, affrontando progressivamente rumore sperimentale, bias sistematici, ambiguità di allineamento e complessità computazionale. La pipeline può quindi essere interpretata come una sequenza di alternative, ciascuna associata a vantaggi e limiti specifici.

La fase iniziale riguarda il controllo di qualità e il trimming, necessari per eliminare basi a bassa qualità e adattatori. Gli strumenti differiscono soprattutto per flessibilità, velocità e granularità delle opzioni.  
- Cutadapt è adatto quando gli adattatori non sono standard o quando serve un controllo preciso, ma può risultare meno efficiente su dataset molto grandi  
- Trimmomatic è ampiamente usato in pipeline consolidate grazie alla struttura modulare, ma richiede configurazioni più verbose  
- AdapterRemoval v2 è efficace nei paired-end perché permette la fusione di reads sovrapposti, migliorando l’accuratezza, ma è meno generalista  
- Atropos estende Cutadapt con maggiore efficienza, ma è meno integrato nei workflow più diffusi  
- fastp integra trimming, filtraggio e report automatici in un solo passaggio, risultando estremamente rapido, ma i default possono introdurre effetti indesiderati se non controllati  

Un problema trasversale è rappresentato dai batch effects, variazioni spurie tra campioni dovute a differenze sperimentali. Strumenti come svaseq e Combat-Seq permettono di ridurre questi bias, aumentando l’affidabilità dell’analisi differenziale, ma con il rischio di rimuovere anche segnali biologici reali se applicati in modo troppo aggressivo.

La fase successiva è l’allineamento, che consiste nell’identificare la regione genomica o trascrittomica da cui proviene ogni read. Questo passaggio è tra i più costosi e complessi, e presenta diverse strategie.

Gli aligner genomici completi producono mapping dettagliati e file BAM, utili per analisi downstream come variant calling o splicing analysis, ma richiedono tempo e memoria elevati.  
- Bowtie2 è veloce ed efficiente grazie a BWT/FM-index, ma non è ottimizzato per reads che attraversano giunzioni di splicing  
- STAR è estremamente rapido e gestisce molto bene lo splicing, risultando ideale per RNA-seq, ma richiede una quantità di memoria molto elevata  
- TopHat2 è oggi meno competitivo perché più lento e meno accurato rispetto ad alternative moderne  
- HISAT2 utilizza un approccio a grafo e hierarchical indexing, offrendo un buon compromesso tra velocità e consumo di memoria  

Quando manca un genoma di riferimento, diventa necessario un assemblaggio de novo del trascrittoma, che consente la scoperta di nuovi trascritti ma introduce ambiguità e maggiore incertezza nella quantificazione.

Accanto agli aligner tradizionali esistono metodi di pseudoalignment, progettati per la quantificazione rapida. Questi approcci evitano il mapping base-per-base e assegnano i reads direttamente ai trascritti compatibili.  
- Kallisto è estremamente veloce e leggero, ideale su larga scala, ma non produce allineamenti completi e quindi non supporta analisi strutturali dettagliate  
- Salmon utilizza un modello probabilistico più ricco e corregge diversi bias (GC, posizionale), risultando spesso più accurato, ma richiede maggiore attenzione nella parametrizzazione  

Dopo l’allineamento o pseudoalignment, la fase di counting consiste nell’assegnazione dei reads a geni o regioni annotate. Questo passaggio determina direttamente la matrice utilizzata per la differential expression analysis e dipende fortemente da come vengono gestiti reads ambigui.  
- HTSeq-count è semplice e trasparente, ma poco scalabile su dataset grandi  
- BEDTools è estremamente flessibile per feature personalizzate, ma meno diretto per pipeline RNA-seq standard  
- featureCounts è molto rapido e ottimizzato per grandi progetti multi-sample, ma presenta una configurazione più complessa  

A partire dalla matrice di conteggi, uno degli obiettivi principali dell’RNA-seq è la differential expression analysis, cioè l’identificazione dei **DEG** (Differentially Expressed Genes). Un DEG è un gene la cui espressione cambia in modo significativo tra due o più condizioni biologiche differenti, come tessuto sano e tumorale, cellule trattate e non trattate, oppure stadi diversi di sviluppo. Questi geni rappresentano il risultato centrale dell’analisi, poiché evidenziano quali componenti molecolari sono coinvolte nei cambiamenti biologici osservati.

In modo schematico, un gene è considerato DEG quando:

$$\text{espressione}_{cond1} \neq \text{espressione}_{cond2}$$

e la differenza risulta statisticamente significativa dopo correzione per falsi positivi.

Per rendere confrontabili i conteggi tra campioni è necessario introdurre un passaggio di normalizzazione, poiché un numero maggiore di reads mappati non implica automaticamente un’espressione più alta. La normalizzazione inter-sample più semplice utilizza scaling factors, cioè fattori moltiplicativi specifici per ciascun campione. Le principali alternative includono:  
- Total Count (TC), che divide i conteggi per la library size totale, ma risulta sensibile a pochi geni altamente espressi  
- Upper Quartile (UQ), che sostituisce la library size con il quartile superiore dei conteggi diversi da zero, riducendo l’influenza degli outlier  
- Median (Med), che utilizza la mediana dei conteggi non nulli, aumentando la robustezza ma perdendo informazione globale  
- DESeq, basato sull’ipotesi che la maggior parte dei geni non sia differenzialmente espressa, e che calcola il fattore come mediana dei rapporti rispetto alla media geometrica  
- TMM (Trimmed Mean of M-values), implementato in edgeR, che confronta ciascun campione con un riferimento calcolando una media pesata di log-ratios dopo trimming  

Esistono anche approcci alternativi come Quantile normalization, che forza distribuzioni simili tra campioni, e RPKM, che corregge anche per la lunghezza genica ma può introdurre bias nelle varianze, soprattutto per geni poco espressi.

Un aspetto cruciale è che i dati RNA-seq sono conteggi interi, non negativi e spesso molto asimmetrici, con una varianza che dipende fortemente dalla media. Un modello iniziale naturale è quello di Poisson:

$$Y_{gi}\sim Poisson(\lambda_{gi})$$

ma nei dati reali si osserva overdispersion, cioè:

$$Var(Y_{gi}) \gg E(Y_{gi})$$

a causa di variabilità biologica e tecnica. Per questo motivo la distribuzione più appropriata è la binomiale negativa, che generalizza Poisson introducendo un parametro di dispersione:

$$Var(Y_{gi})=E(Y_{gi})+\theta E(Y_{gi})^2$$

Questo modello è alla base dei principali strumenti per DEG analysis, in particolare DESeq2 ed edgeR.

In DESeq2 la stabilizzazione della varianza può essere ottenuta anche tramite trasformazioni dedicate (VST, rlog) usate soprattutto per visualizzazione e clustering, mentre il test differenziale rimane basato su conteggi raw e modello NB. edgeR, invece, incorpora direttamente la relazione media-varianza nel modello NB GLM, evitando un passaggio separato di trasformazione e utilizzando logCPM con prior per analisi esplorative.

Un passaggio centrale in entrambi è la shrinkage dispersion estimation, necessaria perché con pochi replicati le stime di dispersione gene-specifiche risultano estremamente instabili. La shrinkage applica un approccio empirical Bayes, che combina una stima globale dispersione-media con la stima individuale del gene, ottenendo un compromesso tra bias e varianza e migliorando il controllo del FDR.

Infine, l’identificazione dei DEG richiede la valutazione statistica tramite p-value, che misura la probabilità di osservare un risultato almeno così estremo assumendo vera l’ipotesi nulla $H_0$. Poiché nell’RNA-seq si effettuano migliaia di test simultanei, è necessario applicare correzioni per confronti multipli. Il metodo più utilizzato è la procedura di Benjamini–Hochberg, che controlla il False Discovery Rate:

$$FDR=E\left(\frac{V}{R}\right)$$

e permette di interpretare un insieme di geni con FDR = 0.05 come un insieme in cui circa il 5% delle scoperte attese sono false, pur senza sapere quali geni nello specifico.

La pipeline RNA-seq si sviluppa quindi come una catena coerente di scelte metodologiche, in cui ogni alternativa modifica il compromesso tra accuratezza statistica, interpretabilità biologica e costo computazionale.
