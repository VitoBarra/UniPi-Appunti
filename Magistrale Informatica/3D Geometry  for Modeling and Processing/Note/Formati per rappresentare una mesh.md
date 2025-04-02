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
##### Polygon soup 
le **Polygon soup** é un array di $n$ __poligoni__ ed ogni poligono é  una array di posizioni + attributi.
é  un approccio molto semplice ma inefficiente siccome ogni vertice condiviso é duplicato per ogni poligono, questo lo rende anche difficile da aggiornare siccome per ogni aggiornamento di un vertice va aggiornato su tutti i poligoni che mantengono una copia di quel vertice.

##### Indexed Mesh
Si divide il concetto di vertice e poligono.
si mantiene un [[array|array]] di vertici detto __Geometry array__ e un array di poligoni
i Poligoni sono rappresentati come una sequenza di referenze ad i vertici nel __Geometry array__
![[Pasted image 20240220212013.png]]



##### Formati
#### Standard tasselation Language 
lo __Standard Tasselation Language__ (STL) salva la mesh come lista di facce (Triangolari) ed ogni faccia è composta da 3 posizioni ovvero i vertici del triangolo e ogni vertice è espresso da 3 coordinate.![[IMG_1176.jpeg]]
Non c è nessuna nozione di connettività  tra i vertici e tutti i vertici condivisi sono duplicati, ciò significa che modificare un vertice diventa un operazione costata siccome bisogna cercare e eventualmente cambiare ogni riferimento a quel vertice.

### Object e Object File format
il formato __object__ e il formato __object file format__ (OFF) questi formati salvano indipendentemente i vertici e i triangoli, Ogni vertice è salvato come 3 coordinate e ogni triangolo ha 3 riferimenti a 3 vertici.
![[IMG_1175.jpeg]]
questo semplifica la modifica dei vertici siccome non c è bisogno di ricercarlo in tutti i triangoli, in più è più efficiente in termini di memoria occupata rispetto alle STL, questo siccome non ci sono vertici duplicati.   

### Face-Base Connectivity
![[IMG_1177.jpeg]]

vertici che tengono posizione e il riferimento ad una faccia
faccine: 3 vertici e riferimento a 3 faccine adiacenti.
Non mantengono edge e questo puo essere un problema.



Edge-base rappresentation:
- Vertici:
	- posizione 
	- 1 edge
![[IMG_1179.jpeg]]




rappresentazione Halfedge-Based:


esiste un rappresentazione puramente matriciali con tante matrici sparse.




