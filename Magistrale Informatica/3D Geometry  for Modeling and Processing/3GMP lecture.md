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




### To point cloud to scalar field
la nuvola di punti deve avere anche le normali. 



# Parametrizazione
Trasformare una mappa del globo nella mappa sul piano 2D è un problema di parametrizazione.



La parametrizazione serve per il textur mapping ama anche per il remeshing con madifiche globali non locali

Trasformare tutti in 2D permette di traportare l immane processing i 3D 



La parametrizazione 

Strategia per introdurre tagli ma questo da mille priblemi


Appattimento della superifice.



Tipo di distorsioni:
- Preservazione degli angoli.
- Preserve l area
- se li preserva entrambi allora è isometrica


Calcolare la distrosione.

si usano le [[Sviluppi di Taylor|espansioni di tailor]], cose fiche

Le parametrizazione dovrebbero essere bigettive in pratica non lo sono quasi mai e va bene cosi





# Tagli





## 3D photo acquisition
si fa con le  foto e falisce nei casi di oggetti laminari, come parti e pelo e punti molto luminiosi o trasparenti. 
per esmpio il vetro non si ritrova nulla di simile da poter riusare per la ricostruzione.












