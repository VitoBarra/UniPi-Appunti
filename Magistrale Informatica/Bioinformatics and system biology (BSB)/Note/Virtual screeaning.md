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
Il **virtual screening** comprende un insieme di metodologie computazionali impiegate nelle fasi iniziali della scoperta di [[Pipeline per lo sviluppo di nuovi farmaci|nuovi farmaci]], con l’obiettivo di identificare composti chimici potenzialmente attivi verso uno specifico bersaglio biologico. 

Il virtual screening rappresenta un’alternativa e un complemento allo al [[high-throughput screening|l’high-throughput screening]], consentendo di analizzare milioni di composti in silico con costi e tempi drasticamente ridotti. Il processo è generalmente gerarchico e prevede una riduzione progressiva dello spazio chimico mediante una combinazione di tecniche.

Un primo livello di filtraggio può essere effettuato tramite [[Design di farmaci basati su farmacofori|screening farmacoforico]], che seleziona i composti in grado di soddisfare un insieme di caratteristiche funzionali e geometriche essenziali per l’interazione con il bersaglio. Successivamente, ulteriori analisi affinano la selezione fino a ottenere un numero ristretto di candidati.

Le metodologie di virtual screening dipendono dalle informazioni disponibili sul sistema biologico. In presenza della struttura tridimensionale del bersaglio, risultano applicabili approcci receptor-based, come il [[docking|docking]] molecolare e i farmacofori basati sul sito di legame. In assenza di strutture sperimentali, il recettore può essere modellato tramite omology modeling. Quando sono noti più ligandi attivi, è possibile adottare approcci ligand-based, che includono farmacofori derivati dai ligandi, metodi di similarità di forma e confronti basati su descrittori molecolari bidimensionali. L’integrazione di approcci differenti consente di aumentare l’affidabilità complessiva del processo di selezione.

Il docking molecolare è una tecnica centrale del virtual screening receptor-based e mira a predire la modalità di legame di un ligando all’interno del sito attivo del bersaglio. Tuttavia, la presenza di numerosi software di docking, basati su algoritmi di ricerca e funzioni di scoring differenti, può generare risultati discordanti. Per affrontare questa variabilità è stato sviluppato l’approccio del **consensus docking**.

![[IMG - Consensus docking.png]]
Nel consensus docking, ciascun ligando viene dockato utilizzando più software indipendenti e le pose di legame ottenute vengono confrontate tramite misure geometriche, in particolare la RMSD. Due pose sono considerate simili quando la RMSD reciproca è inferiore a una soglia tipicamente pari a $2\text{Å}$. Il livello di consenso è definito come il numero di software che convergono sulla stessa posa di legame. Un elevato livello di consenso indica una maggiore affidabilità della modalità di legame predetta e una probabilità più alta che il ligando sia effettivamente attivo sul bersaglio. Questo approccio permette di integrare in modo sinergico i vantaggi dello screening computazionale con quelli dello [[high-throughput screening|screening fisico]], massimizzando l’efficienza nella selezione di hit e lead nella [[Pipeline per lo sviluppo di nuovi farmaci|pipeline di sviluppo dei farmaci]].
