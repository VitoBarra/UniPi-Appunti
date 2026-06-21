---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Cytoscape EnrichmentMap - Tool per visualizzare enrichment
---
**EnrichmentMap** è un'app di Cytoscape usata per visualizzare risultati di functional enrichment come reti di gene set. È utile quando una lista di risultati contiene molti pathway o termini ridondanti e si vuole capire la struttura globale dell'arricchimento.

In EnrichmentMap:
- ogni nodo rappresenta un gene set, un pathway o un termine funzionale;
- un arco collega due nodi quando condividono molti geni;
- cluster di nodi simili rappresentano temi biologici comuni.

Questo approccio trasforma una lunga tabella di enrichment in una rete più leggibile, dove è possibile riconoscere gruppi funzionali ricorrenti.

Input tipici:
- risultati di ORA o GSEA;
- gene set usati nell'analisi;
- statistiche di significatività;
- lista di geni e valori associati, ad esempio $\log_2FC$.

Output tipici:
- rete di gene set arricchiti;
- cluster funzionali;
- visualizzazioni esportabili;
- annotazioni manuali o semi-automatiche dei gruppi biologici.

EnrichmentMap è indicato quando:
- i risultati di enrichment sono lunghi e ripetitivi;
- si vuole confrontare più condizioni o contrasti;
- serve una visualizzazione di insieme;
- si vuole integrare enrichment con reti e annotazioni in Cytoscape.

Limiti:
- richiede più preparazione rispetto a tool web rapidi;
- la qualità della rete dipende dalla qualità dei gene set e delle soglie;
- cluster simili non implicano pathway indipendenti;
- resta necessario interpretare biologicamente i gruppi e non solo la topologia.

Vedi anche: [[WebGestalt - Tool per pathway enrichment]], [[STRING - Tool per reti PPI ed enrichment]], [[REVIGO - Tool per semplificazione GO]].
