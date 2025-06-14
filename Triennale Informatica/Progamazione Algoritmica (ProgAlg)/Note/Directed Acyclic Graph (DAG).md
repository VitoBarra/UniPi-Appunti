---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: "[[Strutture Dati]]"
---
#  Directed Acyclic Graph (DAG)
---
un **Directed Acyclic Graph***(**DAG**) è un tipo di [[grafi|grafo]] **orientato** caratterizzato dall'**assenza di cicli**. Ogni arco possiede una direzione definita, indicata da una coppia ordinata di vertici $(u, v)$, che rappresenta un collegamento dal nodo $u$ al nodo $v$. L'assenza di cicli implica che non esiste alcun percorso che parta da un nodo e, seguendo gli archi nella loro direzione, ritorni al nodo stesso.

Formalmente, un DAG è definito come una coppia $G = (V, E)$, dove:
- $V$ è l'insieme dei vertici;
- $E \subseteq V \times V$ è l'insieme degli archi orientati.

Una proprietà distintiva dei DAG è la possibilità di effettuare un *ordinamento topologico* dei vertici. Questo ordinamento consiste in una sequenza $v_1, v_2, \dots, v_n$ tale che, per ogni arco $(v_i, v_j) \in E$, risulta $i < j$. Tale proprietà è utilizzata in numerosi contesti applicativi, come la pianificazione di attività, la risoluzione di dipendenze e l'analisi di flussi di dati.

Un altro aspetto rilevante riguarda la rappresentazione dei DAG mediante matrici di adiacenza o liste di adiacenza. Nella matrice di adiacenza $A$ di dimensione $|V| \times |V|$, l'elemento $A_{ij}$ vale 1 se esiste un arco da $v_i$ a $v_j$, altrimenti vale 0.

In relazione alla struttura ad albero, un DAG può essere considerato una generalizzazione. Mentre un [[Alberi|albero]] è un DAG in cui ogni nodo, ad eccezione della radice, ha esattamente un predecessore, in un DAG generico un nodo può avere molteplici predecessori o nessuno. Tuttavia, non essendoci cicli, la relazione di dipendenza rimane transitiva e ben definita.

Dal punto di vista algoritmico, sui DAG possono essere eseguite efficientemente operazioni come la ricerca di cammini più lunghi, il calcolo del flusso massimo e la determinazione delle componenti fortemente connesse, sfruttando l'assenza di cicli per garantire la terminazione dei procedimenti iterativi e ricorsivi.

