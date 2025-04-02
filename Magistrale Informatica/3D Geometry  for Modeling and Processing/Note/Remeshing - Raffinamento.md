---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Remeshing - Raffinamento
---
Gli algoritmi di [[Meshing e il Remeshing|remeshing]] di __raffinamento__ sono algoritmi dove a partire da una [[Mesh Poligonali|mesh]] se ne genera una altra con più dettaglio, solitamene piu [[Smoothness di una superfice|smooth]] 
questa categoria di [[Algoritmi|algoritmi]] si possono dividere in dure direzioni ortogonali 

| Primale                                 | Duale                                                                   |
| --------------------------------------- | ----------------------------------------------------------------------- |
| ogni faccia viene divisa in sotto facce | ogni faccia viene generata a partire da una faccia un vertice o un edge |
![[Pasted image 20241111184425.png]]

| Approssimante                                                                                                                                      | interpolante                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| I vertici della mesh originale sono considerati solo come punti di controllo, la nuova mesh quindi non deve necessariamente passare per quei punti | I vertici della mesh originale vengono fissati e la nuova mesh viene costruita interpolando tra questi vertici mantenuti fissi. |
![[Pasted image 20241111184527.png]]



|               |                      Primale                      |                                                         | Duale                                           |
| ------------- | :-----------------------------------------------: | :-----------------------------------------------------: | ----------------------------------------------- |
|               |                     Tiangoli                      |                       rettangoli                        |                                                 |
| Approssimante |      [[Algoritmo di Remeshing Raffinamento - Loop\|loop]]      | [[Algoritmo di Remeshing Raffinamento - Catmur-Clark\|Catmur-Clark]] | [[Algoritmo di Remeshing Raffinamento - DooSabin\|DooSabin]] |
| Interpolante  | [[Algoritmo di Remeshing Raffinamento - Butterfly\|butterfly]] |                         Kobbelt                         | Midedge                                         |

