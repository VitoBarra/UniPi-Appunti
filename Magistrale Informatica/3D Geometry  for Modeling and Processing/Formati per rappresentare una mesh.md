---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Formati per rappresentare una mesh
---


STL : molto brutto poche operazioni semplici da fare, solo una collezione di faccie


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




