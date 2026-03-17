---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Protein-Protein interaction network
---
La **Protein-Protein interaction network** è una [[Biological networks|rete biologiche]] che rappresenta le interazioni tra proteine all'interno della cellula, cioè della struttura dell'**interactoma**.
È tipicamente modellata come un grafo non orientato $G=(V,E)$, eventualmente pesato, in cui i nodi rappresentano proteine e gli archi rappresentano interazioni fisiche dirette o associazioni funzionali annotate nei database.
- **Nodi**: proteine.
- **Archi**: interazioni **proteina-proteina**.
- **Peso dell'arco**: score di confidenza $w_{ij}\in[0,1]$.
- **Natura della rete**: in genere statica, non orientata e usata soprattutto per analisi strutturali e topologiche.
Una Protein-Protein interaction network non descrive direttamente causalità o dinamica temporale, ma l'organizzazione delle connessioni molecolari, la presenza di moduli funzionali e la posizione topologica delle proteine nella rete. Per questo è uno dei modelli principali delle e viene studiata con strumenti della [[Network Science|network science]].

Le informazioni contenute in una PPI network possono derivare da fonti diverse:
- **interazioni fisiche**: binding o contatto diretto tra proteine;
- **associazioni funzionali**: relazioni inferite da co-espressione, text mining, pathway condivisi o altre evidenze indirette.

Quando l'obiettivo è studiare distanze topologiche, cammini minimi o prossimità tra moduli, è preferibile considerare soprattutto interazioni fisiche ad alta confidenza, perché sono più interpretabili come connessioni elementari del network.
Dal punto di vista topologico, le PPI mostrano spesso proprietà tipiche delle reti biologiche complesse:
- **degree distribution** spesso eterogenea, frequentemente compatibile con una [[Variabili Aleatorie Notevoli - Potenza o Zipf|legge di potenza]] $P(k)\sim k^{-\gamma}$;
- presenza di **hub**, cioè proteine con grado elevato;
- **clustering coefficient** relativamente alto, indice di organizzazione modulare;
- cammini medi brevi, compatibili con comportamento **[[Network Science|small-world]]**;
- presenza di nodi ponte identificabili tramite **betweenness centrality** $$C_B(v)=\sum_{s\neq v\neq t}\frac{\sigma_{st}(v)}{\sigma_{st}}$$ dove $\sigma_{st}$ è il numero di cammini minimi tra $s$ e $t$ e $\sigma_{st}(v)$ quelli che attraversano $v$.

Gli hub contribuiscono alla connettività globale della rete, mentre i nodi con alta betweenness collegano moduli diversi e possono agire come **bottleneck**. In ambito biologico questi nodi sono spesso rilevanti perché una loro alterazione può compromettere la comunicazione tra funzioni cellulari differenti.

Una PPI network può essere costruita integrando insiemi di proteine di interesse e recuperando le loro interazioni da database specializzati. Dopo la costruzione della rete, i nodi possono essere distinti in:
- proteine appartenenti a un insieme biologicamente caratterizzato;
- proteine target di un farmaco;
- proteine intermedie di collegamento;
- proteine aggiunte come vicini di primo o secondo ordine per connettere i moduli.

In analisi di **network medicine** una malattia è rappresentata come un **disease module**, cioè l'insieme delle proteine associate a quella patologia nell'interactoma, mentre un farmaco è rappresentato come un **drug module**, cioè l'insieme dei suoi target proteici. Il confronto tra questi moduli consente di valutare relazioni topologiche tra malattia e trattamento.

Una misura centrale è la **network proximity**, cioè la distanza tra due moduli $A$ e $B$. Una formulazione possibile è la media dei cammini minimi tra tutte le coppie di nodi dei due insiemi: $$d(A,B)=\frac{1}{|A||B|}\sum_{a\in A}\sum_{b\in B}d(a,b)$$ dove $d(a,b)$ è la lunghezza del cammino minimo tra $a$ e $b$. Valori piccoli indicano vicinanza topologica tra i moduli, mentre valori grandi indicano separazione.

Accanto alla proximity si usa anche la **separation**, che confronta la distanza inter-modulo con la coesione interna dei moduli stessi e permette di distinguere situazioni di sovrapposizione, vicinanza o separazione topologica.

L'analisi delle PPI networks viene svolta sia con strumenti visuali sia con librerie di analisi dei grafi:
- strumenti visuali per esplorare componenti connesse, hub, cluster e distribuzione dei nodi;
- librerie per calcolare grado, diametro, clustering coefficient, centralità, shortest paths e distanze tra moduli.

Le PPI networks hanno anche alcuni limiti strutturali:
- dipendono dalla qualità e completezza dei database;
- possono includere interazioni mancanti o falsi positivi;
- non modellano direttamente dinamica, contesto cellulare o verso causale dell'interazione;
- richiedono integrazione con altri modelli quando si vogliono studiare regolazione, cinetica o dinamica temporale.

Per questo vengono spesso affiancate a [[Gene Regulatory Networks (GRN)|Gene Regulatory Networks]], [[Cell pathways|pathways]] e dati di espressione, così da collegare organizzazione topologica, funzione biologica e comportamento del sistema.
