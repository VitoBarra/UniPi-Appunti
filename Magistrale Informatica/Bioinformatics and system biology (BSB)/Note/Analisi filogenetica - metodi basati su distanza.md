---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi filogenetica - Metodi basati su distanza
---
I **metodi basati su distanza** costituiscono una delle principali classi di algoritmi per la costruzione di alberi nell’ambito dell’[[Analisi filogenetica]]. In questo approccio, l’informazione contenuta in un insieme di sequenze viene riassunta mediante una misura quantitativa di dissimilarità, trasformando il problema filogenetico in un problema di costruzione di un albero che approssimi una matrice di distanze pairwise.

Il flusso concettuale di questi metodi segue una sequenza standard:
- costruzione di un [[Allineamento di sequenze multiple (MSA)|allineamento multiplo]];
- calcolo di una **matrice di distanza** tra tutte le coppie di sequenze;
- costruzione dell’albero che meglio rappresenta tali distanze;
- valutazione dell’albero tramite una funzione obiettivo.

Un primo elemento fondamentale è la [[Definizione di distanza|definizione della distanza]] tra due sequenze allineate, poiché i [[Analisi filogenetica - Metodi basati su distanza|metodi basati su distanza]] si fondano sulla trasformazione delle differenze osservate tra sequenze in una misura quantitativa di divergenza. In questo contesto si può utilizzare la [[Proportional distance (p-distance)|proportional distance (p-distance)]] come descrizione immediata delle differenze, oppure adottare distanze evolutive corrette, come la [[Distanza di Jukes-Cantor|distanza di Jukes-Cantor]], quando si intende interpretare tali differenze in termini di cambiamento evolutivo accumulato e costruire alberi filogenetici più coerenti con un modello di sostituzione.

Una volta calcolata la matrice delle distanze $D$, la costruzione dell’albero può essere formulata come un [[Problemi di ottimizzazione|problema di ottimizzazione]] in cui la funzione obiettivo misura quanto bene l’albero ricostruito approssima le distanze osservate. Una forma tipica è la minimizzazione dell’errore quadratico:$$
\text{score}(T)=\sum_{i,j\in S}\bigl(d_{i,j}(T)-D_{i,j}\bigr)^2
$$dove $d_{i,j}(T)$ sono le distanze indotte dall’albero e $D_{i,j}$ quelle della matrice. Lo spazio delle possibili topologie cresce rapidamente con il numero di sequenze, rendendo il problema complessivamente [[Classi di complessita - NP-Hard|NP-hard]] e motivando l’uso di algoritmi euristici. 

Per costruire l’albero a partire dalla matrice di distanze vengono impiegati algoritmi di **clustering gerarchico bottom-up**, che aggregano progressivamente sequenze o cluster di sequenze. due algoritmi usati sono
- [[Analisi Filogenetica  - Metodo su distanza UPGMA]]
- [[Analisi Filogenetica  - Metodo su distanza Neighbour-Joining]]