---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Cytoscape
---
**Cytoscape** è una piattaforma software per visualizzare, analizzare e annotare reti biologiche. In bioinformatica viene usata soprattutto per lavorare con [[Biological networks|reti biologiche]], [[Protein-Protein interaction network (PPIN)|reti PPI]], pathway, reti di gene set e risultati di enrichment.

L'idea centrale è rappresentare dati biologici come un grafo:
- i **nodi** rappresentano entità biologiche, ad esempio geni, proteine, metaboliti, pathway o gene set;
- gli **archi** rappresentano relazioni, ad esempio interazioni fisiche, associazioni funzionali, appartenenza allo stesso pathway o similarità tra gene set;
- gli **attributi** dei nodi e degli archi contengono informazioni quantitative o qualitative, come fold change, p-value, score di confidenza, tipo di interazione o sorgente del dato.

Cytoscape non è solo un visualizzatore: permette di integrare dati esterni, filtrare reti, applicare layout, calcolare misure topologiche e costruire rappresentazioni più interpretabili di risultati complessi.

## Screenshot

Schermata generale dell'interfaccia di Cytoscape, con area centrale per la rete e pannelli laterali/inferiori per gestione, attributi e tabelle:

![[IMG - Cytoscape main window.png]]

Esempio di rete PPI costruita con [[STRING - Tool per reti PPI ed enrichment|STRING]], un caso d'uso tipico che può essere esportato o importato in Cytoscape:

![[IMG - Protein-Protein interaction network - STRING.png]]

## Uso tipico

Un workflow comune consiste in:
1. ottenere una lista di geni, proteine o pathway da un'analisi, ad esempio [[Analisi RNA-seq|RNA-seq]];
2. costruire una rete usando database o tool esterni, ad esempio [[STRING - Tool per reti PPI ed enrichment|STRING]];
3. importare la rete in Cytoscape;
4. associare attributi sperimentali ai nodi, ad esempio $\log_2FC$ e p-value;
5. visualizzare moduli, hub, cluster o pathway arricchiti;
6. esportare figure o tabelle per interpretazione biologica.

## App e plugin

Cytoscape è estendibile tramite app. Alcune app permettono di collegare direttamente Cytoscape a database biologici o a risultati di analisi:
- **STRING app**: importa reti PPI e associazioni funzionali da STRING;
- **EnrichmentMap**: visualizza risultati di enrichment come rete di gene set;
- app per clustering, annotazione funzionale, analisi topologica e integrazione di pathway.

[[Cytoscape EnrichmentMap - Tool per visualizzare enrichment|EnrichmentMap]] è quindi un caso specifico d'uso di Cytoscape, non Cytoscape stesso.

## Link utili

- [Sito ufficiale Cytoscape](https://cytoscape.org/)
- [Manuale utente Cytoscape](https://manual.cytoscape.org/en/stable/)
- [Quick Tour di Cytoscape](https://manual.cytoscape.org/en/stable/Quick_Tour_of_Cytoscape.html)
- [Tutorial ufficiali Cytoscape](https://tutorials.cytoscape.org/)
- [Cytoscape App Store](https://apps.cytoscape.org/)
- [stringApp per Cytoscape](https://apps.cytoscape.org/apps/stringapp)
- [EnrichmentMap per Cytoscape](https://apps.cytoscape.org/apps/enrichmentmap)
- [Cytoscape Automation](https://automation.cytoscape.org/)

## Cosa permette di osservare

In una rete biologica Cytoscape aiuta a identificare:
- **hub**, cioè nodi con molte connessioni;
- **moduli o community**, cioè gruppi di nodi densamente connessi;
- **bottleneck**, cioè nodi importanti per collegare parti diverse della rete;
- pathway o funzioni biologiche concentrate in specifiche regioni della rete;
- relazioni tra dati di espressione, interazioni molecolari e annotazioni funzionali.

Queste osservazioni sono utili per passare da una lista di risultati a una struttura interpretabile, ma non dimostrano da sole causalità biologica.

## Limiti

- La qualità dell'analisi dipende dalla qualità della rete di partenza.
- Layout visivamente convincenti non implicano automaticamente significato biologico.
- Reti dense possono essere difficili da interpretare senza filtri o clustering.
- Le interazioni importate da database possono essere incomplete, biasate o derivate da sorgenti eterogenee.
- Serve distinguere tra interazioni fisiche dirette e associazioni funzionali.

Vedi anche: [[Protein-Protein interaction network (PPIN)]], [[STRING - Tool per reti PPI ed enrichment]], [[Cytoscape EnrichmentMap - Tool per visualizzare enrichment]], [[Network Science]], [[Biological networks]].
