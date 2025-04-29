---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Ricostruzione Moving last square
---
L’algoritmo **Ricostruzione Moving Least Square** è un metodo di [[Ricostruzione di superfici del mondo reale con rappresentazioni point base|ricostruzione di superfici]] basato su [[Point Cloud (nuvola di punti)|nuvole di punti]], che si distingue per la capacità di ottenere superfici smooth a partire da dati rumorosi. Questo approccio si fonda sull’idea dei minimi quadrati locali pesati, dove la funzione di fitting viene costruita non globalmente, ma localmente, su finestre mobili nel dominio.

L’idea di base consiste nell’effettuare un *local fitting* di una polinomiale su un sottoinsieme di punti campionati, utilizzando una funzione di peso $\theta$ che decresce con la distanza dal punto centrale di analisi. In questo modo, ogni punto contribuisce al fitting in misura proporzionale alla sua vicinanza al punto di interesse. Tale funzione di peso è solitamente una gaussiana.

L’algoritmo procede iterativamente seguendo tre passi principali:

1. Si determina il piano locale che meglio approssima il sottoinsieme dei punti vicini a un punto $r$, minimizzando la distanza quadrata tra ciascun punto $p_i$ e il piano definito da una normale $n$ e da una distanza scalare $t$:

   $$
   \min_{n, t} \sum_{i=1}^N \left( \langle n, p_i - r - tn \rangle \right)^2 \, \theta\left( \|p_i - r - tn\| \right)
   $$

   Questo primo passo è un problema non lineare e serve a identificare la migliore orientazione locale del piano di appoggio.

2. Una volta ottenuta la proiezione dei punti sul piano locale (rappresentato nello spazio parametrico 2D), si esegue un fitting polinomiale nel dominio locale:

   $$
   \min_g \sum_{i=1}^N \left(g(x_i, y_i) - f\right)^2 \, \theta\left( \|p_i - q\| \right)
   $$

   Dove $g$ è la polinomiale di fitting, $(x_i, y_i)$ sono le coordinate dei punti proiettati sul piano, e $q$ è il punto proiettato ortogonalmente da $r$ sul piano.

3. Si aggiorna infine la posizione di $r$ muovendolo nella direzione della normale del piano, aggiustata dalla funzione $g$ valutata in zero:

   $$
   r \leftarrow q + g(0, 0) \cdot n
   $$

   Questo aggiornamento sposta il punto verso una stima più liscia della superficie, contribuendo a un progressivo *smoothing* della nuvola di punti.

L’illustrazione sottostante mostra la sequenza geometrica di operazioni. I punti $p_i$ (neri) vengono proiettati sul piano locale $H$ secondo la normale $n$. La curva $g$ rappresenta la polinomiale interpolante, che approssima localmente la superficie. Il punto $r$ viene quindi spostato nella nuova posizione $q + g(0,0)n$, producendo un effetto di regolarizzazione:

![[IMG - Ricostruzione Moving last square esempio.png]]

Questo processo non solo consente di ottenere una rappresentazione implicita della superficie, ma permette anche un efficace *resampling* della nuvola di punti. La nuvola viene infatti rielaborata spostando i punti originali verso la superficie smooth stimata, riducendo così il rumore e migliorando la qualità geometrica del dato:

![[IMG - Ricostruzione Moving last square resampling.png]]
Tale metodo trova applicazione sia nella ricostruzione vera e propria della superficie, sia nella preparazione dei dati per ulteriori operazioni di analisi o rendering.
