---
type: nota
course: Programmazione e Algoritmica
topic: 
tags: ProgAlgo Data_Structure
---

Prev: [[Programmazione Algoritmica (ProgAlg)]]

# Albero struttura dati
---
In [informatica](https://it.wikipedia.org/wiki/Informatica), un **albero** è una[[Strutture Dati| struttura dati]] che si riconduce al concetto di [albero con radice](https://it.wikipedia.org/wiki/Albero_(grafo)#Arricchimenti_degli_alberi) presente nella [[Grafo struttura dati|teoria dei grafi]]. Un albero si compone di due tipi di sottostrutture fondamentali: il **nodo**, che in genere contiene informazioni, e l'**arco**, che stabilisce un collegamento gerarchico fra due nodi: si parla allora di un **nodo padre** dal quale esce un arco orientato che lo collega ad un **nodo figlio**.

Si chiede inoltre che ogni nodo possa avere al massimo un unico arco entrante, mentre dai diversi nodi possono uscire diversi numeri di archi uscenti. Si chiede infine che l'albero possegga un unico nodo privo di arco entrante: questo nodo viene detto **radice** (*root*) dell'albero. Ogni nodo che non presenta archi uscenti è detto **foglia** (*leaf node*) e in ogni albero finito, cioè con un numero finito di nodi, si trova almeno un nodo foglia. Ovviamente, un nodo può essere contemporaneamente padre (se ha archi uscenti) e figlio (se ha un arco entrante, ovvero se è diverso dalla radice).

Solitamente ogni nodo porta con sé delle informazioni e molto spesso anche una chiave con cui è possibile identificarlo univocamente all'interno dell'albero. L'**altezza** o **profondità** dell'albero è il massimo delle lunghezze dei suoi **cammini massimali**, cammini che vanno dalla radice alle sue foglie.


