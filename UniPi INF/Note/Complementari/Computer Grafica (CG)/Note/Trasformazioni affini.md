---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Trasformazioni affini
---
#### Trasformazione affine
nella _computer grafica_ usiamo la trasformazioni usate sono  un sotto insieme delle trasformazioni possibili, e sono quelle più facili e sono dette _[[Trasformazioni Geometriche affini|trsformazioni affini]]_ 
una _trasformazione_ è _affine_ se
1. mantiene la _colinearita_ dei punti, ovvero due punti se sono sulla stessa linea ci restano anche dopo la trasformazione 
2. Mantiene le _proprozioni_ ovvero presi 3 punti $p_{1},p_{2},p_{3}$ sulla stessa linea il rapporto $$\frac{\|p_{2}-p_{1}\|}{\|p_{3}-p_{1}\|}$$ è preservato dopo la _trasformazione_.

![[IMG_0731.jpeg]]

#### Interpretazione geometrica
le _trasformazioni affini_ sono delle _[[Applicazioni Lineari|trasformazioni lineari]]_ che pero non hanno piu un _punto di origine fisso_ che è quindi libero di variare ed essere spostato per _traslazione_.

Usando le [[Coordinate omogenee|coordinate omegenee]] viene espresso dalla matrice $$\begin{bmatrix}
a_{xx} & a_{xy}   & v_{x} \\
a_{yx}  & a_{yy} & v_{y}  \\
0 & 0 & 1  
\end{bmatrix}$$dove la prima sotto matrice $2\times 2$ e rappresenta la parte _lineare_ ovvero _rotazione_ e _scaling_ e l ultima colonna rappresenta la parte _[[Sottospazii affini|affine]]_ ovvero la _traslazione_ del punto d origine 
![[IMG_0756.jpeg]]