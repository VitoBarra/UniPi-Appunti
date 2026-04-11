---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Shading
---
lo __Shading__ è il processo di calcolare la quantità di luce e quindi il [[Rappresentazione di colori|colore]] per [[Pipeline di Rasterizazione|frammento]] sono di 3 tipi
- __Flat Shading__: la luce è calcolata per ogni faccia della [[Mesh Poligonali|mesh]]
- __Gauraud shading__: la luce è calcolata per vertice e poi interpolata
- __Phong shading__: la luce è calcolata per frammento


##### Flat shading
La luce e calcolata una volta per faccia e cio porta al fatto che tutta una faccia abbia lo stesso colore.
![[IMG - Illuminazione - Shading 1.png]]
Questo porta a rendere piu evidente la tasselizazione della [[Mesh Poligonali|mesh]]
![[IMG - Illuminazione - Shading 2.png]]

##### Gauraud shading
la luce viene calcolata nei [[Computer grafica - Primitive Geometriche|vertici]] e poi interpolata con [[Interpolazione di vertici - Coordinate Baricentriche|coordinate baricentriche]] nel [[Mesh Poligonali|triangolo]]
![[IMG - Illuminazione - Shading 3.png]]
![[IMG - Illuminazione - Shading 4.png]]
nella pipeline 
![[IMG - Illuminazione - Shading 5.png]]

![[IMG - Illuminazione - Shading 6.png]]
non sempre pero risolve tutti i problemi 
![[IMG - Illuminazione - Shading 7.png]]
e il risultato dipende fortemente dalla tasselizazione che si usa e è molto probabile che gli [[Illuminazione - Interazione della luce con la materia|riflessi speculare]] vengano completamente sbagliati
![[IMG - Illuminazione - Shading 8.png]]



#### Phong shading
con il __Phong shading__ si interpola la [[Normale di una superfice parametrica|normale]] tra i vertici e si poi calcola il colre nel fragment shader.
e quindi nella [[Pipeline di Rasterizazione|pipeline di rasterizazione]]
![[IMG - Illuminazione - Shading 9.png]]
bisogna stare attenti siccome l interpolazione di [[Normale di una superfice parametrica|normali]] non restituisce sempre vettori di lunghezza 1, vanno quindi normalizati prima di essere usati
![[IMG - Illuminazione - Shading 10.png]]
#### Confronto

![[IMG - Illuminazione - Shading 11.png]]
- __Grauraud shading__: piu veloce da calcolare siccome i vertici sono meno dei frammenti
- __Phong shading__: piu costoso da calcolare ma risultati molto piu precisi
![[IMG - Illuminazione - Shading 12.png]]