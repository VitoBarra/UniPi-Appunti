---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# REVIGO - Tool per semplificazione GO
---
**REVIGO** è un tool per ridurre e visualizzare liste ridondanti di termini [[Gene Ontology (GO)|GO]]. È utile dopo un'analisi di functional enrichment, perché GO produce spesso molti termini simili o collegati da relazioni parent-child.

REVIGO prende in input termini GO associati a una misura di significatività, ad esempio p-value o adjusted p-value, e raggruppa termini semanticamente simili. L'obiettivo non è rifare l'enrichment, ma sintetizzare i risultati già ottenuti.

Input tipici:
- lista di termini GO;
- p-value, adjusted p-value o score associato;
- scelta della misura di similarità semantica;
- specie o database di riferimento quando richiesto.

Output tipici:
- lista ridotta di termini rappresentativi;
- scatterplot semantico;
- treemap;
- network di termini;
- tabelle esportabili.

REVIGO è indicato quando:
- l'enrichment produce decine o centinaia di termini GO;
- molti risultati sono ridondanti;
- serve una sintesi leggibile per relazione, esame o discussione biologica;
- si vuole separare il segnale principale dai termini parent-child ripetitivi.

Limiti:
- non sostituisce la scelta corretta del background;
- non corregge errori nella lista di geni o nel mapping degli ID;
- la riduzione semantica può nascondere dettagli biologici specifici;
- va usato come strumento di sintesi, non come prova statistica aggiuntiva.

Vedi anche: [[clusterProfiler - Tool per pathway enrichment]], [[Gene Ontology (GO)]], [[Cytoscape EnrichmentMap - Tool per visualizzare enrichment]].
