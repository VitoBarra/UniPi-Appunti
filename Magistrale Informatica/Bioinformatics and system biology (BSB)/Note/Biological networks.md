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
I **Biological networks** sono rappresentazioni astratte dei **sistemi biologici** in cui entità molecolari sono modellate come nodi e le loro relazioni come archi, con l’obiettivo di descrivere organizzazione, dinamica e funzionalità della cellula a diversi livelli di astrazione.
![[IMG - Tipi di Biological networks.png]]
In biologia computazionale e [[Bioinformatics and Systems Biology (BSB)|Systems Biology]] si distinguono tre grandi classi di reti, che differiscono per natura dei nodi, tipo di interazione e livello di dettaglio dinamico.

1. **[[Gene Regulatory Networks|Gene Regulatory Networks]] (GRNs)**: descrivono relazioni di regolazione tra geni, ossia influenze che determinano l’attivazione o l’inibizione dell’espressione genica.
    - Nodi: geni (spesso fattori di trascrizione o geni target).  
    - Archi: attivazione (+) o inibizione (−), tipicamente orientati.  
    - Livello: logico/qualitativo (stati discreti), talvolta esteso a modelli quantitativi.  
2. **[[Cell pathways|Cell pathways]]**: descrivono processi cellulari come insiemi di reazioni biochimiche interconnesse; formalmente sono modellati tramite [[Chemical Reaction Network (CRN)|Chemical Reaction Network]].
    - Nodi: specie molecolari (proteine, metaboliti, complessi, RNA).  
    - Archi: reazioni chimiche che trasformano reagenti in prodotti.  
    - Livello: quantitativo/dinamico, spesso modellato tramite equazioni differenziali o modelli stocastici.  
3. **[[Protein-Protein interaction network]] (PPI networks)**: descrivono interazioni fisiche o associazioni funzionali tra proteine all’interno dell’interactoma.
    - Nodi: proteine.  
    - Archi: interazioni di binding fisico o associazioni funzionali (tipicamente non orientate).  
    - Livello: strutturale/topologico, talvolta pesato da score di confidenza.  
Relazione tra i tre livelli:
- Le GRNs operano a livello informazionale, modellando la regolazione dell’espressione genica.  
- I pathways descrivono la dinamica biochimica delle trasformazioni molecolari nel tempo.  
- Le PPI networks catturano l’architettura delle interazioni fisiche tra proteine, evidenziando moduli e organizzazione funzionale.  

Questi tre tipi di reti rappresentano livelli complementari di descrizione dello stesso sistema biologico e costituiscono la base per analisi strutturali, dinamiche e funzionali nei modelli di biologia dei sistemi.