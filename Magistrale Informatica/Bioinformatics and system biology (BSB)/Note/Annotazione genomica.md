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
