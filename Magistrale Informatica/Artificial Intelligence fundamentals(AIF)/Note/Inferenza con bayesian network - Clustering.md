---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza con bayesian network - Clustering
---
L’**[[Inferenza con bayesian network| inferenza con bayesian network]] per clustering** si basa sulla trasformazione della rete in una struttura ad albero attraverso la combinazione di nodi in insiemi detti *cluster nodes*. L’obiettivo è ottenere una rete equivalente in forma di *polytree*, riducendo la complessità computazionale dell’inferenza. Tale approccio, noto anche come *clustering join tree algorithm*, permette di calcolare in modo più efficiente le probabilità posteriori di tutte le variabili del modello.

Il principio fondamentale consiste nel raggruppare i nodi della rete originale in *meganodi* o *cluster*, ciascuno dei quali rappresenta una combinazione di variabili. Se una rete presenta connessioni multiple, i nodi correlati vengono uniti in un unico cluster, in modo che la struttura risultante rispetti la condizione di aciclicità tipica del *polytree*. Ogni *meganodo* assume valori corrispondenti alle combinazioni congiunte delle variabili che lo compongono, e le relazioni di dipendenza vengono ridefinite di conseguenza.

Una volta costruita la rete di cluster, l’inferenza richiede un algoritmo specifico, poiché i metodi ordinari non possono gestire nodi che condividono variabili comuni. L’elaborazione avviene attraverso una forma di propagazione vincolata, in cui si impone che i *meganodi* adiacenti concordino sulle distribuzioni di probabilità delle variabili condivise. Questo processo di coordinamento locale consente di mantenere la coerenza globale delle probabilità posteriori.

La procedura, pur mantenendo la natura [[Classi di complessita - NP-hard|NP-hard]] del problema, consente di ridurre il tempo di calcolo complessivo da $O(n^2)$, come nel caso dell’eliminazione variabile applicata iterativamente, a $O(n)$ per l’intera rete clusterizzata. Tale efficienza è dovuta alla gestione congiunta delle variabili e alla struttura ad albero che elimina le ridondanze computazionali. Tuttavia, quando la rete originale presenta una complessità intrinseca elevata, le tabelle di probabilità condizionate associate ai *meganodi* possono crescere esponenzialmente in dimensione, riflettendo la difficoltà strutturale del modello.

