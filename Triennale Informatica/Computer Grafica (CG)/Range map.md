---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Range map
---
Le **range map** sono un modo per [[Rappresentazione di modelli 3D|rappresentare oggetti in 3D]] **point base**d. e sono delle [[Point Cloud (nuvola di punti)|point cloud]] **strutturate**


Una **range map** è definita come una collezione di sample da una superficie, l'[[Insiemi Matematici|insieme]] è strutturato infatti. I 3D scanners producono una serie di height field densi e strutturati, ovvero una griglia regolare $(X, Y)$ di punti in cui ciascuno è associato a un valore di distanza $Z$.

Si puo fare una triangolazione banale seguendo la griglia.
![[IMG - Range map.png]]


Una delle problematiche delle [[range map|range map]] è il fatto che l'[[Acquisizione modelli 3D dal mondo fisico|acquisizione]] di due parti del oggetto anche messe nello stesso [[Frames|frame di riferimento]] tendono a non essere allineate.
![[IMG - mesh zippering.png]]
