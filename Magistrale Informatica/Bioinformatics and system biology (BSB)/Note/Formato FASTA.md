---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato file FASTA
---
Il **formato FASTA** è uno dei formati più semplici e diffusi per la rappresentazione di sequenze biologiche. Esso fornisce una vista semplificata delle sequenze, descrivendo una o più sequenze [[Nucleotidi|nucleotidiche]] o [[Proteine|proteiche]] in forma testuale. La struttura minimale del formato lo rende particolarmente adatto allo scambio di dati e all’utilizzo come input per numerosi algoritmi di [[Analisi di sequenze]].  Il formato non include annotazioni strutturali o funzionali, ma rappresenta esclusivamente la sequenza come una stringa di simboli biologici. Questa caratteristica lo rende complementare ai formati di annotazione, che associano significato biologico a specifiche regioni della sequenza.


Un file FASTA è costituito da una successione di record indipendenti. Ogni record inizia con una riga di intestazione, identificata dal carattere speciale `>`, seguita da una descrizione della sequenza. Alla riga di intestazione segue la sequenza biologica vera e propria, rappresentata su una o più righe consecutive. La suddivisione su più righe non ha significato biologico, poiché la sequenza è definita dalla concatenazione dei caratteri.
La struttura logica di un record FASTA può essere rappresentata come segue:

```
identificatore e descrizione  
SEQUENZA  
SEQUENZA  
SEQUENZA
```

All’interno dello stesso file possono essere presenti più record, ciascuno dei quali può rappresentare una sequenza diversa. Questa caratteristica consente di includere nello stesso file sequenze di DNA, RNA o proteine, rendendo il formato estremamente flessibile.

La sequenza è rappresentata utilizzando simboli appartenenti agli alfabeti biologici standard definiti dai codici IUB/[[Codici IUPAC per nucleotidi e aminoacidi|IUPAC]]. Le sequenze possono essere nucleotidiche o proteiche e, in contesti come l’[[Allineamento di sequenze|allineamento di sequenze]], possono includere caratteri di gap. Le lettere minuscole sono ammesse e vengono interpretate come equivalenti alle corrispondenti maiuscole. Le cifre numeriche non sono considerate parte valida della sequenza, anche se talvolta compaiono in alcune risorse per indicare posizioni.

Non esiste uno standard univoco per l’estensione dei file FASTA; tuttavia, nella pratica vengono utilizzate convenzioni che riflettono il tipo di sequenza contenuta:

| Estensione        | Contenuto                   |
| ----------------- | --------------------------- |
| .fasta, .fa, .fas | FASTA generico              |
| .fna              | sequenze nucleotidiche      |
| .ffn              | regioni geniche codificanti |
| .faa              | sequenze amminoacidiche     |
| .mpfa             | sequenze proteiche multiple |
| .frn              | RNA non codificante         |
