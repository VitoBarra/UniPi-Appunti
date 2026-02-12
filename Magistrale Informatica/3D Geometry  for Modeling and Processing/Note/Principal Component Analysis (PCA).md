---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Principal Component Analysis (PCA)
---
La **Principal Component Analysis (PCA)** è una tecnica di riduzione dimensionale che permette di descrivere un insieme di punti in uno spazio ad alta dimensione tramite un numero ridotto di direzioni che catturano la maggior parte della variabilità. L’idea è trovare un nuovo sistema di coordinate in cui i dati risultano il più possibile “allineati” lungo assi che spiegano la dispersione principale.

Dato un insieme di vettori $p_i$ con $i=1,\dots,N$, si calcola innanzitutto il centroide:$$c = \frac{1}{N} \sum_{i=1}^{N} p_i$$Questo vettore rappresenta la media dei punti. I dati vengono quindi centrati sottraendo il centroide a ciascun vettore, così che la distribuzione sia riferita all’origine.

La dispersione dei punti attorno al centroide è descritta dalla matrice di covarianza:$$C = \frac{1}{N} \sum_{i=1}^{N} p_i p_i^T - cc^T$$Questa matrice cattura come le diverse dimensioni variano insieme. Le direzioni di massima variabilità si ottengono calcolando gli autovettori di $C$. Gli autovettori associati ai maggiori autovalori identificano le direzioni lungo cui la varianza dei dati è massima. Queste direzioni costituiscono le componenti principali e formano una nuova base ortogonale.

Proiettando i dati sulle prime componenti principali si ottiene una rappresentazione a dimensione ridotta che conserva la maggior parte della struttura di variabilità. In termini geometrici, la PCA può essere interpretata come una rotazione dello spazio dei dati che allinea gli assi con le direzioni di massima dispersione.

![[IMG - Principal component analysis.png]]

![video](https://www.youtube.com/watch?v=FgakZw6K1QQ)