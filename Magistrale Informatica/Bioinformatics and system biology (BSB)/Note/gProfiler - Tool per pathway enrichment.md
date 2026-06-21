---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# gProfiler - Tool per pathway enrichment
---
**g:Profiler** è un tool web e programmatico per functional enrichment, conversione di identificativi e interrogazione di database funzionali. Nel contesto di [[Analisi RNA-seq|RNA-seq]] è utile dopo la produzione di una lista di geni differenzialmente espressi, quando si vuole capire quali funzioni, pathway o annotazioni sono sovra-rappresentate.

Le componenti principali sono:
- **g:GOSt**: esegue enrichment su liste di geni;
- **g:Convert**: converte identificativi tra sistemi diversi;
- **g:Orth**: cerca ortologhi tra organismi;
- **g:SNPense**: collega varianti a geni.

Per l'enrichment, g:Profiler usa tipicamente una lista di geni significativi e restituisce termini arricchiti da database come [[Gene Ontology (GO)|GO]], KEGG, Reactome, WikiPathways, TRANSFAC e altri insiemi di annotazioni.

Input tipici:
- lista di geni, ad esempio Ensembl ID, gene symbol o Entrez ID;
- organismo di riferimento;
- sorgenti di annotazione da interrogare;
- background gene set, se disponibile.

Output tipici:
- termini o pathway arricchiti;
- p-value corretto per test multipli;
- geni della lista che contribuiscono al termine;
- sorgente del termine, ad esempio GO:BP, GO:MF, Reactome o KEGG.

Un punto forte di g:Profiler è la gestione pratica degli identificativi: il tool riconosce molti formati e può aiutare a convertire ID prima dell'enrichment. Questo è importante perché un mapping scorretto può rimuovere geni dalla lista o assegnarli alla specie/database sbagliato.

g:Profiler è indicato quando:
- serve una verifica rapida via web;
- si vuole evitare di configurare subito una pipeline R completa;
- l'analisi richiede conversione di identificativi;
- si vuole usare anche l'API o il pacchetto R `gprofiler2`.

Limiti:
- è meno flessibile di una pipeline completamente controllata in R;
- l'interpretazione resta sensibile al background scelto;
- come tutti i tool di enrichment, dipende dalla copertura e qualità delle annotazioni disponibili.

Vedi anche: [[clusterProfiler - Tool per pathway enrichment]], [[WebGestalt - Tool per pathway enrichment]], [[Enrichr - Tool per pathway enrichment]].
