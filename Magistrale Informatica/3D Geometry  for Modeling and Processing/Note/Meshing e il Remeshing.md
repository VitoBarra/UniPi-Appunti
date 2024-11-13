---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Meshing e il Remeshing
---
Il __Meshing__ è un applicazione del __3D geometry processing__ e si occupa di trasformare una superfice ideale continua in una [[Mesh Poligonali|mesh]] discreta facendo in modo che la mesh approssimi quella superfice originale. Il __Remeshing__ invece si occupa di trasformare una mesh in una mesh simile in modo che la nuova possa rispettare una qualche proprietà.

Uno casi in cui Il __Remeshing__ è utile è quando i triangoli di una mesh non sono ben fatti ovvero, il rapporto tra le lunghezze dei lati e della base è molto alto o uno degli angoli è vicino a $180\degree$ siccome in questi casi molte dello operazioni sono [[Problemi Mal Condizionati|mal condizionati]] problema che non c è se i triangoli sono quasi equilateri  ![[Pasted image 20241110154938.png]] 
Altre applicazioni importanti sulle mesh  sono:
 - __[[Remeshing - Raffinamento|Raffinamento]]__ (o __suddivisione__): Aggiungere informazione in modo da avere una mesh simile al originale ma espressa con più poligoni.
 - __[[Remeshing - Semplificazione|Coarsening]]__ (o __semplificazione__): Eliminare del informazione mantenendo comunque una certa similarità alla mesh originale. Si esprime quindi la mesh con meno poligoni


