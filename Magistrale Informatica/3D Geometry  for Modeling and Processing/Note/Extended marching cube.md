---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Extended marching cube
--- 
Nel [[Marching cube|Marching cube]] uno dei principali limiti dell'assunzione di [[Interpolazione Trilineare|trilinearità]] interna a una cella cubica emerge in presenza di forti discontinuità nella superficie che si intende rappresentare. Un esempio tipico è il caso in cui una superficie presenti un angolo netto, come un angolo di 90 gradi all'interno del cubo. In questi casi, la ricostruzione effettuata con il metodo classico individua correttamente i punti di intersezione tra la superficie e gli spigoli della cella, ma la superficie risultante risulta inevitabilmente smussata, perdendo le alte frequenze e i dettagli geometrici caratteristici della struttura originale.![[IMG - Marching cube algoli vivi.png]]Per affrontare tale problematica si ricorre a una versione estesa dell'algoritmo, denominata comunemente "**Extended Marching Cube**".

La strategia adottata prevede l'uso delle [[Normale di una superfice parametrica|normali]] ai punti di intersezione tra la cella e la superficie. In particolare, per ogni punto di intersezione, oltre alla distanza dal campionamento, si considera anche la normale locale alla superficie. Queste informazioni aggiuntive permettono di determinare se, all'interno della stessa cella, vi siano variazioni significative nell'orientamento della superficie. Quando la differenza angolare tra due normali supera una certa soglia prefissata, si riconosce la presenza di una discontinuità.

Per modellare correttamente queste situazioni, si introduce un ulteriore vertice all'interno della cella e si procede a una [[Problemi di ottimizzazione|minimizzazione]] del errore quadratico rispetto ai piani definiti dalle normali e dai punti di intersezione.  ![[IMG - Marching cube angoli vivi con normali.png]]si riesce a preservare fedelmente anche gli angoli vivi, mantenendo una ricostruzione della superficie molto più aderente alla forma originaria. ![[IMG - Marching cube confronto con versione estesa.png]]