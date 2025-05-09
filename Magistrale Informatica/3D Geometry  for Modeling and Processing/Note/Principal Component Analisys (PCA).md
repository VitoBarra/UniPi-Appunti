---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Principal Component Analisys (PCA)
---
Given a collection of points {pi}, form the co-variance matrix:

Compute eigenvectors of matrix C
![[IMG - Principal component analysis.png]]


Le equazioni presentate rappresentano concetti fondamentali nell'analisi statistica multivariata, in particolare nel calcolo delle proprietà distributive di un insieme di vettori. La prima equazione definisce il centroide, mentre la seconda descrive la dispersione dei dati attorno a questo punto centrale.

Il centroide $c$ di un insieme di $N$ vettori $p_i$ è dato dalla media aritmetica:

$$c = \frac{1}{N} \sum_{i=1}^{N} p_i$$

Questo vettore medio rappresenta il baricentro geometrico dell'insieme di punti nello spazio considerato. La notazione utilizzata mostra chiaramente come si calcoli la somma di tutti i vettori $p_i$ per $i$ che va da 1 a $N$, divisa poi per il numero totale di elementi.

La seconda equazione introduce la matrice di covarianza $C$, che misura come i dati si distribuiscono attorno al centroide:

$$C = \frac{1}{N} \sum_{i=1}^{N} p_i p_i^T - cc^T$$

Il termine $p_i p_i^T$ rappresenta il prodotto esterno di ciascun vettore con la propria trasposta, mentre $cc^T$ è il prodotto esterno del centroide con se stesso. La differenza tra la media di questi prodotti esterni e il prodotto del centroide fornisce una misura della dispersione dei dati.

Queste equazioni trovano applicazione in numerosi campi, dall'elaborazione di segnali all'analisi di pattern, dove la comprensione della distribuzione spaziale dei dati è fondamentale. La struttura matriciale della seconda equazione è particolarmente importante per analizzare le relazioni tra diverse dimensioni dei dati.