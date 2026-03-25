---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Protein-Protein interaction network (PPIN)
---
La **Protein-Protein interaction network** (**PPIN**) è una [[Biological networks|rete biologica]] che rappresenta le interazioni tra proteine all'interno della cellula, cioè la componente proteica dell'[[Interactomics|interactoma]]. È tipicamente modellata come un grafo non orientato $G=(V,E)$, eventualmente pesato, in cui i nodi rappresentano proteine e gli archi rappresentano interazioni fisiche dirette o associazioni funzionali annotate nei database.
- **Nodi**: [[proteine|proteine]] (il proteoma)
- **Archi**: interazioni **proteina-proteina**.
    - **Interazione fisica**: legame bi-fisico diretto tra due proteine.
    - **Associazione funzionale**: relazione indiretta tra proteine coinvolte nello stesso processo biologico, nella stessa via o con profili di co-espressione simili, senza necessariamente un contatto fisico diretto.
- **Peso dell'arco**: score di confidenza $w_{ij}\in[0,1]$.
- **Natura della rete**: in genere statica, non orientata e usata soprattutto per analisi strutturali e topologiche.
La **Protein-Protein interaction network** non descrive direttamente causalità o dinamica temporale, ma l'organizzazione delle connessioni molecolari, la presenza di moduli funzionali e la posizione topologica delle proteine nella rete. Le informazioni rappresentate da questa tipologia di rete vengono prese dai [[Interactomics|database di interazioni]] 

Dal punto di vista topologico, le PPI mostrano spesso proprietà tipiche delle reti biologiche:
- **degree distribution** spesso eterogenea, frequentemente compatibile con una [[Variabili Aleatorie Notevoli - Potenza o Zipf|legge di potenza]] $P(k)\sim k^{-\gamma}$;
- [[Network Science - Community o moduli|organizzazione modulare]]: **clustering coefficient** relativamente alto
- comportamento [[Network Science|small-world]]: ovvero cammini **medi brevi**
- presenza di **hub**: cioè proteine con grado elevato
- presenza di **bottleneck**:  identificabili tramite misure di [[Network science - Misure di centralita|centralità]], in particolare la **betweenness centrality**.
Gli hub contribuiscono alla connettività globale della rete, mentre i **bottleneck** con alta betweenness collegano moduli diversi. In ambito biologico questi nodi sono spesso rilevanti perché una loro alterazione può compromettere la comunicazione tra funzioni cellulari differenti.

Una PPI network può essere costruita integrando insiemi di proteine di interesse e recuperando le loro interazioni da database specializzati. Dopo la costruzione della rete, i nodi possono essere distinti in:
- proteine appartenenti a un insieme biologicamente caratterizzato;
- proteine target di un farmaco;
- proteine intermedie di collegamento;
- proteine aggiunte come vicini di primo o secondo ordine per connettere i moduli.
Quando la PPI network viene usata per confrontare moduli di malattia e moduli di farmaco si entra nel contesto della [[Medicine network|network medicine]], che applica misure topologiche dell'interactoma a problemi di prioritizzazione terapeutica e riposizionamento di farmaci.

Le PPI networks hanno anche alcuni limiti strutturali:
- dipendono dalla qualità e completezza dei database;
- possono includere interazioni mancanti o falsi positivi;
- non modellano direttamente dinamica, contesto cellulare o verso causale dell'interazione;
- richiedono integrazione con altri modelli quando si vogliono studiare regolazione, cinetica o dinamica temporale.
Per questo vengono spesso affiancate a [[Gene Regulatory Networks (GRN)|Gene Regulatory Networks]], [[Cell pathways|pathways]] e dati di espressione, così da collegare organizzazione topologica, funzione biologica e comportamento del sistema.
