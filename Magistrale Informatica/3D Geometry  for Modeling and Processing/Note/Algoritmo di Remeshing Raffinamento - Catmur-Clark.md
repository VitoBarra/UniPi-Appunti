---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Catmur-Clark
---
L' __[[Remeshing - Raffinamento|algoritmo di raffinamento]] Catmur-Clark__ è un algoritmo classificato come __primale__ è __approssimante__ funziona con tutti i  [[Poligoni|poligoni]].


Dal punto di vista combinatorio, (topologico) per ogni elementi nella [[Mesh Poligonali|mesh]] l'algoritmo segue come:
1. Per ogni faccia genera una faccia genera un vertice
2. Per ogni edge genera un  nuovo vertice
3. Per ogni vertice non fare nulla.
4. Collega il vertice generato dalla faccia ai vertici generati sugli edge
![[Pasted image 20241111192539.png]]
Questo algoritmo ha la proprietà di trasformare una mesh di poligono generica in una mesh di quadrilateri dopo la prima iterazione sulla mesh. Mentre la valenza di ogni vertice viene preservata. 


Mentre dal punto di vista continuo l algoritmo segue come 
1. Per il vertice generato  dalla faccia $i$ si ha che la posizione $d_i=\cfrac{1}{4}\sum^n_jd_{i,j}$
2. per edge e vertici con valenza $>3$  si  segue la maschera ![[Pasted image 20241111230829.png]]


Questo algoritmo può anche essere implementato in due passi utilizzando un l'algoritmo “__half dual__”.

In più la superfice che si ottiene applicando al infinito questo algoritmo puo essere calcolata in forma chiusa in tempo polinomiale

La superfice risulta smooth [[Z-delME|smooth]] se non ci sono vertici di valenza superiore a $5$

