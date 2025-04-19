---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---
# Da superfici Parametriche a Mesh
---
per convertire una  [[Superfici parametriche|superfice parametrica]] una [[Mesh Poligonali|Mesh Poligonale]] si prendono dei sample dello spazio dei parametri con una incremento arbitrario. ad esempio con un incremento di $0.1$
$(s,t)=(0,0),(0.1,0),\dots,(0,0.1),\dots(1,1)$ e per ognuno di questi si aggiunge un vertice nel punto $S(s,t)$ e si crea il vettore delle [[Normale di una superfice parametrica|normali]] per ogni vertice. Connettendo tutti i vertici si ottiene la mesh finale e cambiando l incremento dei sample possiamo cambiare la qualità della mesh
![[Pasted image 20240224003054.png]]

