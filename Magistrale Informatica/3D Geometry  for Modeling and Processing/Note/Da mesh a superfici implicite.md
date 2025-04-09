---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Da mesh a superfici implicite
---
Si puo trasformare una [[Mesh Poligonali|mesh poligonale]] in una [[Superfici implicite|rappresentazione implicita]]. Per fare ciò si utilizzano i **signed distance field** ovvero un campo scalare.
per costruire **signed distance field** si "*posa*" una griglia sullo spazio 3D e ogni punto della griglia è un *punto di campionamento*. I valori presi rappresentano la **distanza** dal punto di campionamento e la mesh. Quindi i valori del campo sono:
- $0$ se il punto di campionamento è sulla mesh.
- $d>0$  si il punto di campionamento è esterno alla [[Mesh Poligonali|mesh]].
- $d<0$ se il punto di campionamento è interno alla [[Mesh Poligonali|mesh]].
![[IMG - da mesh a superfici implicite distance field.png]]
Avere [[Superfici implicite|superfici implicite]] puo essere comodo siccome hanno la proprietà di poter essere facilmente combinate come somme di funzioni.

Un dei problemi di questo metodo e che ritrasformando il **distance field** ottenuto in una [[Mesh Poligonali|mesh]]  introduce molti **artefatti di campionamento**![[IMG - Riconversione in mesh.png]]