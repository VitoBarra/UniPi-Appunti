---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione - Growing Cut
---
il **Growing Cut** un algoritmo per creare per fare tagli in per una [[Parametrizzazione|prametrizzazione]] di una [[Mesh Poligonali|mesh]] 
 
Si parte eseguendo una prima [[Parametrizzazione|parametrizzazione]], si individua il vertice con la distorsione massima e si calcola lo ***shortest path*** da tale vertice al bordo della regione. Questo percorso definisce un nuovo taglio e quindi un nuovo bordo.
Si esegue quindi una nuova parametrizzazione con questo bordo aggiornato e si ripete il processo.
![[IMG - algoritmo Growing Cat.png]]La distorsione, che inizialmente era concentrata viene progressivamente ridistribuita con l’apertura successiva della superficie lungo percorsi che collegano i punti di massima distorsione al bordo.

si può incorrere in problemi di **non [[Applicazioni tra insiemi|bigettività]]** della parametrizzazione: l’apertura può risultare in sovrapposizioni nel piano parametrico, cioè in regioni che si mappano su aree coincidenti. In questi casi, si procede con una **decomposizione ulteriore in regioni separate**, ciascuna delle quali viene trattata come una componente distinta dell’atlas, mantenendo la condizione di iniettività della mappatura locale.



