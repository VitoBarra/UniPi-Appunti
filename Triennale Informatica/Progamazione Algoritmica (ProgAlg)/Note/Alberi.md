---
Course 2: "[[Fondamenti Del Informatica (FDI)]]"
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: "[[Strutture Dati]]"
tags:
  - PEA
---
# Alberi
--- 
 un **albero** è una[[Strutture Dati| struttura dati]] è un tipo di [[Directed Acyclic Graph (DAG)|DAG]] dove in piu è richiesto che ogni nodo abbia al massimo un padre .
  Un albero si compone di due tipi di sottostrutture fondamentali: il **nodo**, che in genere contiene informazioni, e l'**arco**, che stabilisce un collegamento gerarchico fra due nodi: si parla allora di un **nodo padre** dal quale esce un arco orientato che lo collega ad un **nodo figlio**.

Si chiede inoltre che ogni nodo possa avere al massimo un unico arco entrante, mentre dai diversi nodi possono uscire diversi numeri di archi uscenti. Si chiede infine che l'albero possegga un unico nodo privo di arco entrante: questo nodo viene detto **radice** (*root*) dell'albero. Ogni nodo che non presenta archi uscenti è detto **foglia** (*leaf node*) e in ogni albero finito, cioè con un numero finito di nodi, si trova almeno un nodo foglia. Ovviamente, un nodo può essere contemporaneamente padre (se ha archi uscenti) e figlio (se ha un arco entrante, ovvero se è diverso dalla radice).

Solitamente ogni nodo porta con sé delle informazioni e molto spesso anche una chiave con cui è possibile identificarlo univocamente all'interno dell'albero. L'**altezza** o **profondità** dell'albero è il massimo delle lunghezze dei suoi **cammini massimali**, cammini che vanno dalla radice alle sue foglie.





Un **albero** è un grafo non orientato, connesso e aciclico. Questo significa che:
- Esiste sempre un unico cammino tra due vertici qualunque.
- Se si aggiunge un arco, si crea un ciclo.
- Se si rimuove un arco, il grafo diventa disconnesso.

Un **albero radicato** è un albero in cui è stato scelto un vertice speciale chiamato **radice**. Questo impone una gerarchia tra i nodi, con la radice come livello più alto.

Un **albero radicato orientato**, spesso chiamato **DAG (Directed Acyclic Graph)**, è un grafo orientato che non contiene cicli. In un DAG esiste un ordinamento topologico dei nodi, ovvero un ordinamento lineare tale che per ogni arco $(u, v)$, il nodo $u$ precede $v$ nell'ordine.


