---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# 3GMP lecture

Progetti:
- riduzione distorsione con parametrizazione di voronoi. Aggiustare zone distorte.
- Chiusura dei buchi seguendo i la curva della mesh in modo ragionevole.



Tecnologia di acquisizione 
[[Acquisizione modelli 3D dal mondo fisico]]



questi strumenti danno del rumore di acquisizione, il resto del rumore viene dalle “miss registration”, 

Densità di acquisizione 


non campionamento regolare  per oggetti distanti con strumenti time-of-flight 




Ricostruzione della superficie da nuvoli di punti.

Metodi espliciti e metodi impliciti:
esplicit: i punti sono considerati misure estatte

nei metodo implicit: approssimazione si cerca una funzione che i cui zeri sono vicini alla point claud.

i metodi esplicit: sono molto buoni se i punti sono molto buono peggio se c è molto rumore.

i metodi implicit: molto piu resistenti al rumore sucuramente si perde del informazione del oggetto reale.





Variante del alpha shape, Ball pivoting 







Progetto intersezione i due diagrammi di voronoi si fa in classe,




Campionamento gestito in modo generico. si associa un samplere, che solo delle funzoini da calcolare sui vertici nuovi generati. in questi modo ci si posono salvae informaizoni derivate dalla facci ach l ha generata.


#### Marching cube 3D
Problema del ambiguità usando la look up table di 256 cosi




### To point cloud to scalar field
la nuvola di punti deve avere anche le normali. 
