---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Pipeline di Rasterizazione]]"
SubTopic: "[[Trasformazione Frammenti in Pixel]]"
---

# Back Face Culling
---
nella fase della [[Pipeline di Rasterizazione|pipeline di rasterizazione]] di  [[Trasformazione Frammenti in Pixel|trasformazione di frammenti in pixel]] sia ha che nei casi in cui la scena e' fatta di [[Mesh Poligonali#Classificazione mesh|mash chiuse]] e non si puo "entrare" nelle mesh possiamo evitare di renderizare le __back face__, ovvero le face la cui normale punta nella direzione opposta al osservatore.
![[Pasted image 20240216145801.png]]
Per identificare una __back face__ si calcola la norma.
sia $\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p}_2$ un triangolo proiettato nel __near plane__
allora calcolando la norma suoi punti proiettati $\boldsymbol{p}_{0_{xy}},\boldsymbol{p}_{1_{xy}},\boldsymbol{p}_{2_{xy}}$  calcolata come $$N=(\boldsymbol{p}_{1_{xy}}-\boldsymbol{p}_{0_{xy}})
\times (\boldsymbol{p}_{2_{xy}}-\boldsymbol{p}_{0_{xy}})$$
- Se positiva allora __front face__
- se negativa __back Face__

![[Pasted image 20240216150116.png]]
e questo calcolo e' fatto prima della [[Trasformare da Vertici a Frammenti (Rasterizazione)]]
![[Pasted image 20240216150054.png]]
la mesh non deve essere necessariamente chiusa, ma deve smembrarlo. un terreno non e' una mesh chiusa ma se non possiamo andare sotto e' come se lo fosse
![[Pasted image 20240216150906.png]]