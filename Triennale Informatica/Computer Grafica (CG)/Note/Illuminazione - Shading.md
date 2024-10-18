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
![[Pasted image 20240306043614.png]]
Questo porta a rendere piu evidente la tasselizazione della [[Mesh Poligonali|mesh]]
![[Pasted image 20240306043635.png]]

##### Gauraud shading
la luce viene calcolata nei [[Computer grafica - Primitive Geometriche|vertici]] e poi interpolata con [[Interpolazione di vertici - Coordinate Baricentriche|coordinate baricentriche]] nel [[Mesh Poligonali|triangolo]]
![[Pasted image 20240306055550.png]]
![[Pasted image 20240306055802.png]]
nella pipeline 
![[Pasted image 20240306055927.png]]

![[Pasted image 20240306055947.png]]
non sempre pero risolve tutti i problemi 
![[Pasted image 20240306060012.png]]
e il risultato dipende fortemente dalla tasselizazione che si usa e è molto probabile che gli [[Illuminazione - Interazione della luce con la materia|riflessi speculare]] vengano completamente sbagliati
![[Pasted image 20240306060228.png]]



#### Phong shading
con il __Phong shading__ si interpola la [[Normale di una superfice|normale]] tra i vertici e si poi calcola il colre nel fragment shader.
e quindi nella [[Pipeline di Rasterizazione|pipeline di rasterizazione]]
![[Pasted image 20240306060438.png]]
bisogna stare attenti siccome l interpolazione di [[Normale di una superfice|normali]] non restituisce sempre vettori di lunghezza 1, vanno quindi normalizati prima di essere usati
![[Pasted image 20240306060622.png]]
#### Confronto

![[Pasted image 20240306060515.png]]
- __Grauraud shading__: piu veloce da calcolare siccome i vertici sono meno dei frammenti
- __Phong shading__: piu costoso da calcolare ma risultati molto piu precisi
![[Pasted image 20240306043711.png]]