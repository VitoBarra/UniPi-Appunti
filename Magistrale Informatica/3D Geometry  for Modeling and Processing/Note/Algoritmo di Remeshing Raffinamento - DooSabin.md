---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Algoritmo di Remeshing Raffinamento - DooSabin
---
L' __[[Remeshing - Raffinamento|algoritmo di raffinamento]] DooSabin__  è un algoritmo classificato come __duale__ è __approssimante__ funziona con ogni tipo di [[Poligoni|poligono]].

Dal punto di vista combinatorio, (topologico) l'algoritmo segue come:
1. Per ogni faccia genera una faccia piu piccola
2. Per ogni edge genera una faccia adiacente alle facce adiacenti a quel edge
3. Per  ogni vertice associa una faccia [[Poligoni|pologonali]] con $n$ lati quanti erano gli edge incidenti.
	1. ad un vertice su cui incidono $3$ edge viene assegnato un triangolo.
	2. ad un vertice su cui incidono $5$ edge viene assegnato un pentagono.
![[Pasted image 20241111185503.png]]
una proprietà combinatoria di questo algoritmo e che rende il grado (ovvero gli edge incidenti) di ogni vertice pari $4$ 


Mentre dal punto di vista continuo si ha che:
1. Calcolo tutti i punti di mezzo degli edge [[Mesh Poligonali|mesh]] originale $E_i = \cfrac{d_{1i}+d_{1i}}{2}$ 
2. Calcolo tutti i baricentri di ogni  faccia $V_j= \cfrac{1}{n}\sum_{j=1}^n d_{j}$
3. Calcolo i nuovi vertici $d_{i,j}=\cfrac{1}{4}(d_i+E_j+E_{j-1}+V_j)$
![[Pasted image 20241111190903.png]]
Questo algoritmo funziona siccome per ogni vertice vecchio vano calcolati solo vertici nuovi poi si puo passare al prossimo. 



L'effetto globale e che la superfice diventa piu smooth cancellando gli angoli