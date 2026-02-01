---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Virtual screening
---
Il **virtual screening** comprende un insieme di metodologie computazionali impiegate nella [[Pipeline per lo sviluppo di nuovi farmaci|drug discovery]] con l’obiettivo di identificare composti chimici potenzialmente attivi verso uno specifico [[Recettori e ligandi|bersaglio biologico]]. Esso rappresenta un’alternativa e un complemento all’[[high-throughput screening|high-throughput screening]], poiché consente di analizzare milioni di molecole *in silico* con tempi e costi drasticamente ridotti.

Il processo di virtual screening è generalmente **gerarchico** e prevede una riduzione progressiva dello spazio chimico mediante una combinazione di tecniche, fino a ottenere un numero ristretto di candidati (*hit*) da sottoporre a validazione sperimentale.

Un primo livello di filtraggio può essere effettuato tramite [[Modello Farmacoforico|modello farmacoforico]], che seleziona i composti in grado di soddisfare un insieme di requisiti funzionali e geometrici essenziali per l’interazione con il target. Successivamente, i composti selezionati possono essere sottoposti a metodi più accurati, come il [[Docking|docking molecolare]], per predire la modalità di legame e stimare l’affinità di interazione.

Le strategie di **virtual screening** dipendono dalle informazioni disponibili sul sistema biologico. In presenza della struttura tridimensionale del bersaglio, risultano applicabili approcci **receptor-based**, come docking e farmacofori basati sul sito di legame. In assenza di strutture sperimentali, il recettore può essere approssimato mediante *homology modeling*. Quando invece sono noti più ligandi attivi, è possibile adottare approcci **ligand-based**, che includono [[Farmacofori|farmacofori]] derivati dai ligandi, metodi di similarità di forma e confronti basati su descrittori molecolari bidimensionali.

L’integrazione di approcci differenti (screening farmacoforico, docking, consensus strategies) consente di aumentare la robustezza complessiva del processo di selezione e di migliorare la probabilità di identificare nuovi composti attivi.

### Esempi
![[IMG - prima filtraggio usando modello farmacoforo.png]]
![[IMG - Pharmacophore-driven Consensus Docking.png]]