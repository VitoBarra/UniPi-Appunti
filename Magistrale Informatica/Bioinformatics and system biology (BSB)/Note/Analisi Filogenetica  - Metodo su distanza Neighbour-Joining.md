---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi Filogenetica - Metodo su distanza Neighbour-Joining
---
Il **Neighbour-Joining** è un [[Analisi filogenetica - Metodi basati su distanza|metodo basato su distanza]] per l’[[Analisi filogenetica|analisi filogenetica]] progettato per costruire alberi filogenetici senza richiedere che le distanze siano **ultrametriche**. A differenza di UPGMA, esso non assume un tasso evolutivo costante e può quindi essere applicato anche quando le sequenze hanno accumulato cambiamenti a velocità differenti.

L’algoritmo opera a partire da una matrice di distanze pairwise $D$, ma la scelta delle coppie da unire non dipende unicamente dalla distanza minima $D_{i,j}$. Invece, viene valutata anche la posizione relativa di ciascuna sequenza rispetto a tutte le altre, con l’obiettivo di identificare coppie di vicini che minimizzino la lunghezza complessiva dell’albero.

A tal fine, Neighbour-Joining introduce una matrice trasformata $Q$, definita come:
$$
Q_{i,j}=(n-2)D_{i,j}-\sum_{k=1}^n D_{i,k}-\sum_{k=1}^n D_{j,k}
$$
dove $n$ è il numero di sequenze ancora presenti nella fase corrente dell’algoritmo.

La coppia $(i,j)$ che minimizza $Q_{i,j}$ viene interpretata come la migliore candidata a formare un nodo interno dell’albero. Dopo l’unione, la matrice delle distanze viene aggiornata e il procedimento viene ripetuto fino a ottenere un unico albero che connette tutte le sequenze.

Neighbour-Joining rappresenta quindi un metodo efficiente e flessibile per la ricostruzione filogenetica basata su distanze, particolarmente utile quando non è plausibile assumere ultrametricità o un modello di molecular clock.
