---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Formati per rappresentare una mesh
---

<<<<<<< HEAD:Magistrale Informatica/3D Geometry  for Modeling and Processing/Formati per rappresentare una mesh.md

STL : molto brutto poche operazioni semplici da fare, solo una collezione di faccie
=======
#### Strutture dati per le mesh

##### Polygon soup
é  un array di $n$ __poligoni__ ed ogni poligono é  una array di posizioni + attributi.
é  un approccio molto semplice ma inefficiente siccome ogni vertice condiviso é duplicato per ogni poligono, questo lo rende anche difficile da aggiornare siccome per ogni aggiornamento di un vertice va aggiornato su tutti i poligoni che mantengono una copia di quel vertice.

##### Indexed Mesh
Si divide il concetto di vertice e poligono.
si mantiene un [[array|array]] di vertici detto __Geometry array__ e un array di poligoni
i Poligoni sono rappresentati come una sequenza di referenze ad i vertici nel __Geometry array__
![[Pasted image 20240220212013.png]]



##### Formati
STL : molto brutto poche operazioni semplici da fare, solo una collezione di facce
>>>>>>> main:Magistrale Informatica/3D Geometry  for Modeling and Processing/Note/Formati per rappresentare una mesh.md


obj, OFF: lista di vertici e lista di vertici per faccia.


face-Base Connectivity: 
vertici che tengono posizione e il riferimento ad una faccia
faccine: 3 vertici e riferimento a 3 faccine adiacenti.
Non mantengono edge e questo puo essere un problema.



Edge-base rappresentation:
- Vertici:
	- posizione 
	- 1 edge




rappresentazione Halfedge-Based:


esiste un rappresentazione puramente matriciali con tante matrici sparse.




