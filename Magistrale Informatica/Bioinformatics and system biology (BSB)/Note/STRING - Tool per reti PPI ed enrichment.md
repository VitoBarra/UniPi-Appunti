---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# STRING - Tool per reti PPI ed enrichment
---
**STRING** (**Search Tool for the Retrieval of Interacting Genes/Proteins**) è un database e web tool per esplorare reti di interazione proteina-proteina (**PPI**). Non nasce come tool specifico per [[Analisi RNA-seq|RNA-seq]], ma è spesso usato dopo una differential expression analysis per interpretare una lista di geni o proteine in termini di rete.

Dato un insieme di geni o proteine, STRING costruisce una rete in cui:
- i nodi rappresentano proteine;
- gli archi rappresentano associazioni funzionali o fisiche;
- le interazioni possono derivare da esperimenti, database, co-espressione, text mining o predizioni.

STRING include anche functional enrichment sui nodi della rete, usando sorgenti come [[Gene Ontology (GO)|GO]], KEGG, Reactome e altri database. Questo permette di collegare una lista di geni differenzialmente espressi a processi biologici e pathway, ma anche di vedere se i prodotti proteici tendono a formare un modulo funzionale.

Input tipici:
- lista di geni o proteine;
- organismo;
- soglia di confidenza degli archi;
- eventuale scelta delle fonti di evidenza.

Output tipici:
- rete PPI;
- cluster o moduli funzionali;
- termini GO/pathway arricchiti;
- score di interazione;
- file esportabili per Cytoscape.

STRING è indicato quando:
- si vuole capire se i geni DE formano un modulo proteico coerente;
- interessa l'organizzazione delle interazioni oltre alla lista di pathway;
- si vuole esportare una rete verso Cytoscape;
- si cercano ipotesi su proteine centrali o gruppi funzionali.

Limiti:
- molte interazioni sono associazioni funzionali, non necessariamente legami fisici diretti;
- i database PPI sono incompleti e biasati verso proteine molto studiate;
- una rete densa non implica automaticamente causalità;
- risultati di enrichment e rete vanno interpretati insieme alla qualità delle evidenze.

Vedi anche: [[Protein-Protein interaction network (PPIN)]], [[Cytoscape EnrichmentMap - Tool per visualizzare enrichment]], [[Enrichr - Tool per pathway enrichment]].
