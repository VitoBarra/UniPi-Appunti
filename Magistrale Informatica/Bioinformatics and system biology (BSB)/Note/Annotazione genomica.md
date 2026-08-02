---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Annotazione genomica
---
Un'**annotazione genomica** e' l'associazione di informazioni biologiche a specifiche coordinate di un [[Genoma|genoma]]. Senza annotazioni, una sequenza genomica e' principalmente una lunga stringa di nucleotidi; con le annotazioni, alcune regioni diventano interpretabili come [[Gene|geni]], trascritti, esoni, introni, regioni codificanti, promotori o elementi regolativi.

Le annotazioni permettono quindi di passare dalla sequenza grezza alla rappresentazione biologica del genoma. Sono fondamentali per collegare una posizione genomica a una funzione, a un prodotto molecolare o a un possibile ruolo regolativo.

## Sequenza e annotazione

La sequenza genomica descrive l'ordine delle basi nucleotidiche. L'annotazione descrive invece cosa si conosce o si ipotizza su intervalli specifici della sequenza. Per esempio, una regione puo' essere annotata come gene, un suo sottointervallo come esone e una porzione dell'esone come regione codificante.

Questa separazione e' importante perche' la sequenza e le annotazioni possono essere aggiornate indipendentemente. La stessa sequenza di riferimento puo' ricevere annotazioni diverse a seconda della banca dati, del metodo predittivo o dell'evidenza sperimentale usata.

## Tipi di annotazione

Le annotazioni genomiche possono essere distinte in due categorie principali:

- **annotazione strutturale**: identifica la posizione e l'organizzazione di elementi genomici, come geni, trascritti, esoni, introni, CDS e UTR;
- **annotazione funzionale**: associa agli elementi annotati informazioni biologiche, come funzione del gene, prodotto proteico, pathway, domini, termini [[Gene Ontology (GO)|GO]] o evidenze sperimentali.

In molti casi le annotazioni combinano entrambe le dimensioni: descrivono dove si trova una feature e che ruolo biologico potrebbe avere.

## Formati

Le annotazioni genomiche vengono rappresentate con formati standard, in modo da poter essere usate da strumenti diversi. I formati piu' rilevanti in questo contesto sono:

- [[GFF - Formato per annotazione genomica|GFF/GTF]], che rappresenta annotazioni come feature associate a coordinate genomiche;
- [[GenBank - Formato per annotazione genomica|GenBank]], che integra sequenza, metadati e annotazioni nello stesso file.

In un modello modulare, la sequenza puo' essere conservata in un file [[Formato FASTA|FASTA]] e le annotazioni in un file GFF/GTF separato. In un modello integrato, invece, sequenza e annotazioni sono distribuite nello stesso file.

## Uso nelle analisi

Le annotazioni genomiche sono usate per interpretare i risultati delle analisi. In [[Analisi RNA-seq|RNA-seq]], per esempio, permettono di trasformare read allineate al genoma in conteggi per gene o trascritto. Nei genome browser permettono di visualizzare geni, esoni, trascritti e regioni regolative lungo le coordinate genomiche. Nell'analisi di varianti permettono di stabilire se una mutazione cade in una regione codificante, regolativa o intergenica.

La qualita' delle annotazioni influenza direttamente l'interpretazione biologica: annotazioni incomplete, incoerenti o non aggiornate possono produrre conteggi sbagliati, assegnazioni ambigue o conclusioni biologiche deboli.

## Versioni delle annotazioni e differenze pratiche

Anche le annotazioni vengono pubblicate in versioni successive, per esempio da **Ensembl** o **GENCODE**. La versione dell'annotazione e la versione del [[Genoma di riferimento|genoma di riferimento]] sono due scelte distinte: GRCh38 definisce la sequenza e il sistema di coordinate, mentre una release come Ensembl 115 definisce quali feature biologiche sono riconosciute su quelle coordinate.

Tra due release dell'annotazione possono cambiare:

- il numero di geni e trascritti conosciuti;
- i confini di geni, esoni, CDS e UTR;
- le isoforme associate a uno stesso gene;
- la classificazione `protein_coding`, lncRNA, pseudogene o altri biotipi;
- nomi, identificativi e relazioni tra gene e trascritto;
- il supporto sperimentale e lo stato di validazione delle feature;
- la presenza di trascritti antisenso e altri RNA non codificanti.

Queste differenze hanno conseguenze pratiche nelle analisi. Una read puo' essere assegnata a un gene con una release recente ma risultare non assegnata con una release piu' vecchia; nuovi trascritti possono aumentare l'ambiguita' tra isoforme; confini esonici diversi possono modificare i conteggi. Cambiando annotazione possono quindi cambiare la matrice di conteggio, il numero di geni testati, i fold change, i geni differenzialmente espressi e i risultati dell'enrichment, anche se le read di partenza sono identiche.

In una pipeline basata su allineamento genomico, strumenti come [[HTSeq-count - Software di quantificazione per RNAseq|HTSeq-count]] usano un file GTF/GFF per decidere a quale feature assegnare gli allineamenti. In una pipeline transcript-level, [[Salmon - Software di allineamento per RNAseq|Salmon]] usa invece le sequenze dei trascritti derivate dall'annotazione: una diversa collezione di isoforme cambia direttamente l'insieme delle possibili origini di ogni read.

## Compatibilita' tra sequenza e annotazione

Il file [[Formato FASTA|FASTA]] e il file [[GFF - Formato per annotazione genomica|GTF/GFF]] devono riferirsi allo **stesso assembly** e usare nomi di cromosomi o contig compatibili. Per esempio, non e' corretto combinare un FASTA GRCh38 con un GTF costruito per GRCh37. Anche differenze come `chr1` rispetto a `1` possono impedire agli strumenti di associare correttamente sequenza e feature.

Per rendere un'analisi riproducibile bisogna quindi documentare almeno:

- assembly del genoma, per esempio GRCh38;
- sorgente e release dell'annotazione, per esempio Ensembl 115;
- tipo di riferimento usato, genomico o trascrittomico;
- eventuali filtri applicati a biotipi, contig o trascritti.
