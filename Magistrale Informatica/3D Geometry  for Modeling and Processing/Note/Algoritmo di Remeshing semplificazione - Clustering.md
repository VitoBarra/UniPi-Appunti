---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Algoritmo di Remeshing semplificazione - Clustering
---
Il **Vertex Clustering**, è una tecnica di [[Remeshing - Semplificazione|semplificazione]] delle [[Mesh Poligonali|mesh]] che consiste nel rilevare e unificare *cluster* di vertici vicini. Questa unificazione si basa su una griglia discreta e sulla troncatura delle coordinate, riducendo così la complessità geometrica.

Tutte le facce della mesh originaria che presentano due o tre vertici appartenenti allo stesso cluster vengono eliminate, poiché non rappresentano più una superficie valida dopo l’unificazione.

È importante notare che questa tecnica **non preserva la topologia**: alcune facce possono degenerare in spigoli o punti, e il [[genus|genus]] della superficie può cambiare. Inoltre, l’approssimazione ottenuta dipende dalla risoluzione della griglia utilizzata, rendendo difficile prevedere con esattezza il numero finale di facce della mesh semplificata. spesso genera situazioni non [[Manifolds|manifold]]

![[IMG - Vertex Clustering.png]]

Questo tipo di algoritmo funziona bene per generare i [[livelli di dettagli (LOD)|livelli di dettagli (LOD)]] soprattutto per distanze estreme, un esempio con una lampada:  
![[IMG - semplificazoine clustering esempio lampada.png]]