---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Biological networks
---
i **biological networks** sono un ambito applicativo della **[[Network Science|network science]]** e sono rappresentazioni astratte dei **sistemi biologici** in cui entità molecolari sono modellate come **nodi** e le loro relazioni come **archi**, con l’obiettivo di descrivere **organizzazione**, **dinamica** e **funzionalità** della cellula a diversi livelli di astrazione.
Un **biological network** (o **graph**) è una rappresentazione formale delle **interazioni tra entità molecolari**.
- **Nodes (Vertices $V$)** rappresentano le entità biologiche, come **[[Proteine|proteins]]**, **[[DNA Struttura e funzionalità|genes]]** o **metabolites**.  
- **Edges (Links $E$)** rappresentano le **interazioni** o **relazioni funzionali** tra tali entità, ad esempio **physical binding**, **gene regulation** o **metabolic reactions**.
Formalmente una rete biologica può essere rappresentata come un **grafo** $$G = (V, E)$$ dove $V$ è l’insieme dei nodi e $E$ è l’insieme degli archi che connettono coppie di nodi.

 
L’analisi di queste reti consente di studiare proprietà strutturali e funzionali dei sistemi biologici, come **modularità**, **robustezza**, **centralità** e **organizzazione gerarchica**.


In biologia computazionale e [[Bioinformatics and Systems Biology (BSB)|Systems Biology]] si distinguono tre grandi classi di reti, che differiscono per natura dei nodi, tipo di interazione e livello di dettaglio dinamico.
1. **[[Gene Regulatory Networks (GRN)|Gene Regulatory Networks]] (GRNs)**: descrivono relazioni di regolazione tra geni, ossia influenze che determinano l’attivazione o l’inibizione dell’espressione genica.
    - Nodi: geni (spesso fattori di trascrizione o geni target).  
    - Archi: attivazione (+) o inibizione (−), tipicamente orientati.  
    - Livello: logico/qualitativo (stati discreti), talvolta esteso a modelli quantitativi.  
2. **[[Cell pathways|Cell pathways]]**: descrivono processi cellulari come insiemi di reazioni biochimiche interconnesse; formalmente sono modellati tramite [[Chemical Reaction Network (CRN)|Chemical Reaction Network]].
    - Nodi: specie molecolari (proteine, metaboliti, complessi, RNA).  
    - Archi: reazioni chimiche che trasformano reagenti in prodotti.  
    - Livello: quantitativo/dinamico, spesso modellato tramite equazioni differenziali o modelli stocastici.  
3. **[[Protein-Protein interaction network (PPIN)]] (PPI networks)**: descrivono interazioni fisiche o associazioni funzionali tra proteine all’interno dell’interactoma.
    - Nodi: proteine.  
    - Archi: interazioni di binding fisico o associazioni funzionali (tipicamente non orientate).  
    - Livello: strutturale/topologico, talvolta pesato da score di confidenza.  
![[IMG - Tipi di Biological networks.png]]
Relazione tra i tre livelli:
- Le GRNs operano a livello informazionale, modellando la regolazione dell’espressione genica.  
- I pathways descrivono la dinamica biochimica delle trasformazioni molecolari nel tempo.  
- Le PPI networks catturano l’architettura delle interazioni fisiche tra proteine, evidenziando moduli e organizzazione funzionale.  

Questi tre tipi di reti rappresentano livelli complementari di descrizione dello stesso sistema biologico e costituiscono la base per analisi strutturali, dinamiche e funzionali nei modelli di biologia dei sistemi.