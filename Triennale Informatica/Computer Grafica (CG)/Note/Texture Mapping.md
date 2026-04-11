---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture Mapping
---
il __Texture mapping__ è il processo di applicare una [[Texture|Texture]] ad una [[Rappresentazione di modelli 3D|modello 3D]]. Fare ciò è utile siccome ad esempio se volessimo colorare un [[Mesh Poligonali|mesh]] senza le texture dovremmo adattare la geometria, aggiungendo vertici, ai colori che vogliamo ottenere e questo porta velocemente ad un sistema molto inefficiente.

Ad esempio volessimo realizzare una scacchiera con una __texture__ basterebbero 6 quads mentre senza dovremmo fare un vertice per ogni quadrato e quindi ci servono 5+64 quads 
![[IMG - Texture Mapping 1.png]] il risultato è il medesimo ma senza texture stiamo aggiungendo vertici inutilmente.

![[IMG - Texture Mapping 2.png]]

![[IMG - Texture Mapping 3.png]]
il mostrare a schermo una __texture__  significa associare ad ogni pixel qualcosa che è nella [[Texture|texture]] come questo viene fatto dipende dal tipo di modello.
![[IMG - Texture Mapping 4.png]]
Nella pipeline di [[Rendering|rendenring]]
![[IMG - Texture Mapping 5.png]]



#### Texture mapping di una mesh poligonale
per fare __texture mapping__ su una [[Mesh Poligonali|mesh poligonale]] solitamente si assegnano delle coordinate del __[[Texture|texture space]]__ ad un vertice e si [[Interpolazione Lineare|interpola]] tra i vertici per generare le altre coordinate.
![[IMG - Texture Mapping 6.png]]
nel caso di primitive piu complesse si fa il processo di __UV-unwrapping__ ovvero si appiattisce da una superice 3D ad una __texture space__
![[IMG - Texture Mapping 7.png]]





