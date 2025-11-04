---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Ordinamento topologico
---
L’ordinamento topologico è una disposizione lineare dei vertici di un [[grafi|grafo orientato]] aciclico che rispetta la direzione degli archi. In termini formali, dato un grafo $G = (V, E)$, un ordinamento topologico è una sequenza $v_1, v_2, \ldots, v_n$ dei vertici di $V$ tale che per ogni arco $(v_i, v_j) \in E$ risulti $i < j$. Questa condizione assicura che nessun vertice preceda nella sequenza un altro vertice da cui dipende.

Un grafo ammette un ordinamento topologico se e solo se è aciclico, ossia non contiene cicli diretti. La proprietà di aciclicità è dunque condizione necessaria e sufficiente per la sua esistenza. In termini strutturali, tale ordinamento può essere interpretato come una linearizzazione parziale dell’insieme parzialmente ordinato $(V, \prec)$ definito dalla relazione di raggiungibilità, dove $u \prec v$ se esiste un cammino orientato da $u$ a $v$.

L’algoritmo classico per la determinazione di un ordinamento topologico si basa sul conteggio dei gradi entranti. Si consideri per ogni vertice $v$ il suo grado entrante $\text{deg}^-(v)$ e si scelgano iterativamente i vertici con $\text{deg}^-(v) = 0$, eliminandoli insieme ai relativi archi e aggiornando i gradi residui. La sequenza di eliminazione costituisce un ordinamento topologico valido.

Alternativamente, un approccio basato sulla visita in profondità produce lo stesso risultato: eseguendo una DFS e inserendo ciascun vertice nella lista solo dopo aver esplorato tutti i suoi successori, l’inverso della sequenza finale fornisce un ordinamento topologico corretto. Entrambi i metodi hanno complessità temporale $O(|V| + |E|)$ e risultano particolarmente adatti a strutture di dipendenza e compilazione di processi parzialmente ordinati.

L’ordinamento topologico costituisce quindi una rappresentazione lineare coerente con la direzionalità del grafo e con le relazioni di precedenza definite dall’insieme degli archi, garantendo la compatibilità con la struttura aciclica sottostante.
