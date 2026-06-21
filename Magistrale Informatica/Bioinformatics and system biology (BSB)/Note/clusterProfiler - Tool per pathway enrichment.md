---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# clusterProfiler - Tool per pathway enrichment
---
**clusterProfiler** è un pacchetto R/Bioconductor usato per interpretare liste di geni tramite [[Analisi RNA-seq|functional enrichment]] e pathway enrichment. È uno degli strumenti più usati dopo una differential expression analysis con [[DESeq2 - DE per RNAseq|DESeq2]] o [[edgeR - DE per RNAseq|edgeR]], perché lavora bene sia con liste di geni significativi sia con liste rankate.

Supporta due famiglie principali di analisi:
- **ORA (Over-Representation Analysis)**: parte da una lista di geni selezionati e cerca termini o pathway sovra-rappresentati;
- **GSEA (Gene Set Enrichment Analysis)**: usa una lista ordinata di tutti i geni e cerca pathway concentrati in cima o in fondo al ranking.

clusterProfiler può interrogare o integrare sorgenti come [[Gene Ontology (GO)|GO]], KEGG, Reactome, MSigDB e gene set personalizzati. Per questo è adatto quando si vuole mantenere l'analisi dentro una pipeline riproducibile in R.

Input tipici:
- lista di geni significativi, ad esempio geni con $padj < 0.05$;
- lista rankata, ad esempio ordinata per Wald statistic o $\log_2FC$;
- mapping degli identificativi, ad esempio Ensembl, Entrez ID o gene symbol;
- background gene set coerente con i geni effettivamente testati.

Output tipici:
- termini GO o pathway arricchiti;
- p-value e adjusted p-value corretti per test multipli;
- gene ratio e numero di geni associati al termine;
- lista dei geni che supportano ciascun termine.

clusterProfiler include anche funzioni di visualizzazione come dotplot, barplot, enrichment map e cnetplot. Questi grafici aiutano a capire quali termini sono più forti e quali geni contribuiscono a più pathway.

Un vantaggio importante è la funzione `simplify()`, utile per ridurre la ridondanza dei termini GO molto simili. Questo è necessario perché [[Gene Ontology (GO)|GO]] ha una struttura gerarchica a DAG e spesso produce molti termini parent-child quasi equivalenti.

clusterProfiler è indicato quando:
- si vuole una pipeline scriptabile e riproducibile;
- si devono confrontare più contrasti RNA-seq;
- si vogliono usare sia ORA sia GSEA;
- si vuole integrare enrichment, visualizzazione e riduzione della ridondanza nello stesso ambiente R.

Limiti:
- richiede attenzione nel mapping degli ID;
- risultati e database dipendono dalle versioni installate;
- la qualità dell'analisi dipende dalla scelta del background;
- la ridondanza GO va gestita esplicitamente.

Vedi anche: [[gProfiler - Tool per pathway enrichment]], [[WebGestalt - Tool per pathway enrichment]], [[Enrichr - Tool per pathway enrichment]], [[REVIGO - Tool per semplificazione GO]].
