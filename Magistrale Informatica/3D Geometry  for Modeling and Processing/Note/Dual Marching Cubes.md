---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Dual Marching Cubes
---
Il **Dual Marching Cubes** è una variante del [[Marching cube|Marching Cubes]] in cui, invece di costruire triangoli per ogni cella, si definisce un vertice unico per ogni patch che sarebbe stata generata dal [[Marching cube|Marching Cubes]]. Questo approccio si ispira alla dualità topologica: a ogni vertice corrisponde una faccia, a ogni faccia un vertice, mentre gli spigoli rimangono invariati.

Si considerano gruppi di quattro celle che condividono un edge comune, ad esempio uno verticale. Nel Marching Cubes classico, su questo edge si posizionerebbe un vertice ottenuto tramite interpolazione mentre nel **Dual Marching Cubes**, ogni edge condiviso genera più vertici (uno per ogni cella adiacente), formando una patch quadrilatera. Le connessioni tra patch sono definite tramite una look-up table basata sulla configurazione locale dei valori scalari.
![[IMG - visualizazione Dual Marching Cubes.png]]
Questo metodo è più complesso del Marching Cubes tradizionale: l'insorgere di casi ambigui può portare facilmente a superfici non-[[Manifolds (Varieta)|manifold]]. Tuttavia, il Dual Marching Cubes migliora la qualità geometrica, generando patch piccole e ben condizionate anche in situazioni critiche, come superfici vicine a un vertice del cubo.

version con marching cube (sinistra) versione con dual marching cube (destra)
![[IMG - risultato Dual Marching Cubes.png]]



#### Dual Marching Cubes primal conturing
Un'ulteriore evoluzione nel contesto del **Dual Marching Cubes** riguarda la gestione di rappresentazioni volumetriche adattive, introducendo il concetto di **Primal Contouring of Dual Grids**. 

Uno dei limiti principali del [[Marching cube|Marching Cubes]] classico è la sua complessità intrinseca indipendente dalla semplicità della forma del campo scalare: anche in presenza di un campo lineare che descrive un semplice piano, si generano comunque numerosissimi triangolini.

in regioni dove il campo è sufficientemente lineare quindi planare, si può utilizzare una cella più grande evitando raffinatezze inutili.
Rappresentare un campo scalare con un [[Indici Spaziali - Quad-Tree e Oct-Tree|octree]] significa memorizzare i valori solo sui vertici delle celle ordinate gerarchicamete, permettendo una descrizione compatta e precisa. 
![[IMG - Dual Marching Cubes primal conturing.png]]
il **Marching Cubes** assume celle di dimensione **uniforme** e quindi usando questa strategia viene meno il metodo automatico per triangolare delle intersezioni, va quindi riadattato. Infatti /a soluzione adottata consiste nell'interpretare localmente le celle di dimensioni diverse: ogni volta che una cella più grossa è adiacente a una più piccola, si immagina virtualmente che anche la cella più grande sia suddivisa come quella più fine, ma mantenendo il valore costante.
Si applica quindi il **Marching Cubes** su questa struttura virtuale.