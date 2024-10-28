---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Sampling
---

Samplings dello spazio di direzione.

si utiolizza anche per il remasching. 

Sampling sulle distribuzione come random, uniforme e jitteres.


i jitters è un trade off tra sampling randomico e sampling uniforme. si parte da una distribuzione uniforme e si  spostano i piunti di una quantità casuale e limitata.




SAmpling sui domini 2D e superfici. importanti le metriche,.



Poison Disk Sampling. utile ma è regolare questo puo non essere positivo.
-> Dart Throwing: lo fa randomicamente, ma la velocità di convergenza è molto. bassa perche la pro l’abilità di prendere ciò che no nè atTo preso è sempre minore. 

-> Dart Throwing Salloping: si massimizza la probabilità di prender3e aree di cui snon si è fatto ancora il sampling.  salvandodo un boundaries a aggiungendo punti li vanno aggiornate le strutture dati.

-> hierarchical Dart Throwing: si utilizza un quad-Tree


sacapeling non si espande in 3D facilmente mentre hierarchical Dart Throwing si utilizzano un oct-tree


per il dominio di una superficie invece si utilizzano delle metriche come la distanza euclidea e la distanza geodetica:
geodesica è la distanza tra punti percorrendo la superficie.


l hierarchical puo essere espanso ale superfici: funziona bene per casi in cui i punti son vicini male se sono divisi da dati triangolo (da capire meglio riguardare lezione)




Diagrammi di voronoi, e duale del diagramma molto buono. 


i diagrammi di voronoi buono hanno il punto vicino al centroide