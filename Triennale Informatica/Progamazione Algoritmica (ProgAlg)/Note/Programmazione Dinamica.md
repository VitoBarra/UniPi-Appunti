---
Course: "[[Programmazione e Algoritmica (PEA)]]"
topic: 
tags:
  - PEA
---



# Programmazione Dinamica
---
La **programmazione dinamica** è un paradigma algoritmico per la risoluzione di problemi di ottimizzazione e di decisione caratterizzati da una struttura ricorsiva. Essa si basa sulla scomposizione del problema originale in **sottoproblemi più semplici**, le cui soluzioni vengono riutilizzate per costruire la soluzione globale.

Dal punto di vista formale, un problema è affrontabile mediante programmazione dinamica quando soddisfa due proprietà fondamentali. La prima è la presenza di **sottoproblemi sovrapposti**, ossia la ricorrenza degli stessi sottoproblemi in più parti della risoluzione. La seconda è la **proprietà di ottimalità dei sottoproblemi**, secondo cui una soluzione ottimale del problema globale può essere ottenuta combinando soluzioni ottimali dei sottoproblemi. La formulazione di un algoritmo di programmazione dinamica richiede l’introduzione di una **relazione di ricorrenza**, che esprime il valore ottimale di una soluzione in funzione dei valori ottimali di istanze più piccole del problema. Tale relazione definisce la dipendenza strutturale tra i sottoproblemi e costituisce il nucleo matematico dell’approccio. Per evitare ricalcoli ridondanti, i risultati dei sottoproblemi vengono memorizzati in una struttura dati indicizzata, tipicamente una tabella. Questo meccanismo consente di ridurre drasticamente la complessità computazionale rispetto a formulazioni puramente ricorsive, trasformando un’esplorazione esponenziale in un calcolo polinomiale.

Dal punto di vista operativo, la programmazione dinamica viene generalmente implementata secondo un approccio **bottom-up**, in cui i sottoproblemi vengono risolti in ordine crescente di complessità. In questo modo, quando si calcola la soluzione di un sottoproblema, tutte le informazioni necessarie sono già disponibili. L’approccio bottom-up rende esplicita la struttura del problema e garantisce il riutilizzo sistematico delle soluzioni intermedie.
![[IMG - Programmazione Dinamica grafico.png]]

La complessità temporale di un algoritmo di programmazione dinamica dipende dalla cardinalità dello spazio dei sottoproblemi e dal costo di calcolo di ciascuna transizione definita dalla relazione di ricorrenza. Analogamente, la complessità spaziale è determinata dalla quantità di memoria necessaria per memorizzare le soluzioni intermedie. In molti casi, la memoria richiesta può essere ridotta sfruttando proprietà specifiche del problema, senza modificare la correttezza dell’algoritmo.