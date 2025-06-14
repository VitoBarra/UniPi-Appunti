---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# MSA - algoritmi ibridi
---
I **metodi ibridi** per l’**[[Allineamento di sequenze multiple (MSA)|allineamento di sequenze multiple]]** combinano caratteristiche dei [[MSA - Algoritmi progressivi - CLUSTAL|metodi progressivi]] e degli [[MSA - algoritmi iterativi|algoritmi iterativi]], integrando inoltre **rappresentazioni di profilo** e **informazioni globali di consistenza**. L’obiettivo è migliorare la qualità dell’allineamento senza incorrere nella complessità computazionale della ricerca esatta dell’MSA ottimale.

A differenza dei metodi puramente progressivi, nei metodi ibridi l’allineamento non è costruito una sola volta seguendo un albero guida, ma viene **valutato e raffinato** utilizzando informazioni derivate da più confronti pairwise o da modelli probabilistici. Allo stesso tempo, rispetto agli approcci iterativi puri, i metodi ibridi introducono **vincoli strutturali globali** che guidano il processo di riallineamento.

Un elemento centrale dei metodi ibridi è l’uso dei **profili**. Un profilo rappresenta un allineamento parziale o completo mediante una descrizione statistica delle colonne, tipicamente sotto forma di:
- distribuzioni di frequenza dei simboli;
- punteggi medi di sostituzione;
- modelli probabilistici di emissione.

Questo consente di trattare gruppi di sequenze già allineate come singole entità e di eseguire **allineamenti sequenza–profilo** o **profilo–profilo**, riducendo la complessità e migliorando la stabilità del confronto.

Un’altra caratteristica distintiva dei metodi ibridi è l’introduzione del concetto di **consistenza**. In questo approccio, l’allineamento tra due sequenze non viene valutato isolatamente, ma in relazione agli allineamenti con le altre sequenze del dataset. Le corrispondenze che sono supportate da più allineamenti pairwise vengono considerate più affidabili e influenzano maggiormente la costruzione dell’MSA.

Formalmente, la funzione obiettivo non valuta solo il punteggio diretto di una colonna, ma incorpora informazioni globali derivate da una collezione di allineamenti pairwise preliminari. Questo riduce la probabilità di introdurre errori locali e aumenta la coerenza complessiva dell’allineamento.

Dal punto di vista algoritmico, i metodi ibridi seguono spesso uno schema a più fasi:
1. calcolo di allineamenti pairwise tra tutte o parte delle sequenze;
2. estrazione di informazioni di similarità o consistenza;
3. costruzione di un allineamento iniziale (spesso progressivo);
4. raffinamento iterativo guidato dalle informazioni globali.

Questa combinazione consente di ottenere allineamenti di qualità superiore rispetto ai metodi puramente progressivi, specialmente in presenza di sequenze distanti o regioni scarsamente conservate, mantenendo una complessità computazionale gestibile.

Nel contesto dell’MSA, i metodi ibridi rappresentano un compromesso efficace tra **accuratezza**, **robustezza** e **scalabilità**, e costituiscono la base concettuale di numerosi strumenti moderni per l’allineamento di sequenze multiple.
