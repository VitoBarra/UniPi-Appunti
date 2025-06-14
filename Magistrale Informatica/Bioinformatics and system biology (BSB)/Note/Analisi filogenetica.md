---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Analisi filogenetica
---
L’**analisi filogenetica** riguarda lo studio formale e computazionale delle **relazioni evolutive** tra entità biologiche. Essa ha l’obiettivo di ricostruire la **storia evolutiva relativa** di un insieme di sequenze, identificando pattern di divergenza e conservazione che riflettano processi di discendenza comune. Utilizza un [[Allineamento di sequenze multiple (MSA)|allineamento di sequenze multiple]] per individuare un insieme di posizioni omologhe, che costituiscono la base informativa su cui vengono formulate ipotesi evolutive. Le colonne dell’MSA rappresentano caratteri comparabili tra le sequenze e consentono di modellare eventi di mutazione, inserzione e cancellazione.

Si assume che le sequenze considerate derivino da un **antenato comune**, ossia un’entità ipotetica da cui, attraverso eventi successivi di mutazione, inserzione e cancellazione, si sono generate le sequenze osservate. Questa ipotesi introduce una struttura intrinsecamente gerarchica nelle relazioni evolutive, che può essere modellata mediante un **albero filogenetico**. Questo è un **[[Directed Acyclic Graph (DAG)|grafo aciclico connesso]]**, rappresentabile come un albero radicato. Le **foglie** corrispondono alle entità osservate, mentre i **nodi interni** rappresentano **antenati comuni**. La struttura dell’albero è descritta dalla sua **topologia**, che codifica l’ordine delle ramificazioni, mentre le **lunghezze dei rami** possono rappresentare una misura quantitativa della distanza evolutiva.

Un albero filogenetico può rappresentare relazioni tra entità di natura diversa. Nel caso della **filogenesi interspecifica**, le foglie dell’albero corrispondono a 
- **taxa**: unità di classificazione biologica utilizzata per raggruppare organismi a diversi livelli gerarchici (specie, genere, famiglia), rappresentando una categoria astratta di entità evolutivamente correlate.
- **specie**: livello tassonomico fondamentale che identifica un insieme di organismi geneticamente affini, spesso trattato come unità terminale osservabile nei modelli filogenetici.
e l’inferenza viene spesso condotta utilizzando regioni genomiche altamente conservate, come particolari sequenze di [[RNA|RNA]].
![[IMG - albero filogenetico.png]]
Una porzione dell’albero della vita ricostruita finora può essere rappresentata come segue:
![[IMG - albero filogenetico della vita.png]]

La costruzione di alberi filogenetici è stata tradizionalmente basata su caratteristiche **morfologiche**, mentre oggi si fonda prevalentemente su caratteristiche **molecolari**, in particolare sul confronto di geni derivati da antenati comuni. In questo contesto, è fondamentale distinguere tra diverse tipologie di omologia genica.
- Gli **ortologhi** sono geni che divergono a seguito di un evento di speciazione: una singola versione ancestrale del gene si separa in due copie evolutivamente corrispondenti in specie differenti. Gli ortologhi sono particolarmente utili per inferire relazioni tra specie, poiché riflettono direttamente la storia di divergenza interspecifica.
- I **paraloghi**, invece, derivano da eventi di duplicazione genica all’interno della stessa specie. Dopo la duplicazione, le copie possono evolvere funzioni differenti. I paraloghi possono essere utilizzati per ricostruire filogenesi interne a una specie o per studiare l’evoluzione di famiglie geniche, ma non rappresentano necessariamente la storia di speciazione tra organismi.
![[IMG - Orthologues e paralogues.png]]

Costruire un **[[Analisi filogenetica|albero filogenetico]]** può essere visto come un [[Problemi di ottimizzazione|problema di ottimizzazione]], in cui si ricerca la struttura ad albero che meglio spiega i dati osservati secondo un criterio formale espresso da una **funzione obiettivo**. La scelta della funzione obiettivo consente di classificare i principali algoritmi filogenetici in famiglie metodologiche distinte.
- **[[Analisi filogenetica - Metodi basati su distanza|metodi basati su distanza]]**, che trasformano le differenze tra sequenze in una matrice di distanze pairwise e costruiscono l’albero che meglio approssima tali distanze globali, secondo criteri come la minima evoluzione o procedure di tipo *Neighbor-Joining*.
- **[[Analisi filogenetica - Massima parsimonia|massima parsimonia]]**, che selezionano l’albero che spiega i dati con il minor numero complessivo di cambiamenti evolutivi sui caratteri osservati, ossia quello che richiede il numero minimo di mutazioni per giustificare le differenze tra sequenze.
- **[[Analisi Filogenetica - Massima verosimiglianza|statistici e bayesiani]]**, che adottano modelli espliciti di evoluzione delle sequenze per stimare l’albero. In questo contesto, la **massima verosimiglianza** individua la topologia che massimizza la probabilità dei dati osservati, mentre l’inferenza bayesiana campiona una distribuzione a posteriori sugli alberi, permettendo anche di quantificare l’incertezza associata alle ricostruzioni.
