---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# WebGestalt - Tool per pathway enrichment
---
**WebGestalt** (**WEB-based GEne SeT AnaLysis Toolkit**) è un tool web, disponibile anche come pacchetto R, per analisi di functional enrichment e pathway enrichment. È utile nel downstream di [[Analisi RNA-seq|RNA-seq]] quando si vuole interpretare una lista di geni o una lista rankata collegandola a pathway e annotazioni note.

Supporta più strategie di analisi:
- **ORA (Over-Representation Analysis)**: usa una lista di geni selezionati;
- **GSEA (Gene Set Enrichment Analysis)**: usa una lista rankata;
- **NTA (Network Topology Analysis)**: integra informazione di rete quando disponibile.

Questa varietà lo rende adatto quando si vuole confrontare più approcci di enrichment nello stesso ambiente, senza limitarsi a una sola strategia.

Input tipici:
- lista di geni significativi per ORA;
- lista rankata per GSEA;
- organismo;
- database o gene set di riferimento;
- background gene set, quando appropriato.

Output tipici:
- pathway o termini arricchiti;
- p-value e adjusted p-value;
- geni osservati per ciascun termine;
- grafici e report scaricabili.

WebGestalt è indicato quando:
- si vuole un'interfaccia web completa;
- si vogliono confrontare ORA e GSEA;
- si desidera un report già organizzato;
- si lavora con utenti che preferiscono un tool interattivo rispetto a una pipeline solo script.

Limiti:
- la riproducibilità dipende dalla documentazione precisa di parametri, database e versione;
- il background va scelto con attenzione;
- l'output può essere lungo e ridondante, soprattutto con [[Gene Ontology (GO)|GO]].

Vedi anche: [[clusterProfiler - Tool per pathway enrichment]], [[gProfiler - Tool per pathway enrichment]], [[Enrichr - Tool per pathway enrichment]], [[Cytoscape EnrichmentMap - Tool per visualizzare enrichment]].
