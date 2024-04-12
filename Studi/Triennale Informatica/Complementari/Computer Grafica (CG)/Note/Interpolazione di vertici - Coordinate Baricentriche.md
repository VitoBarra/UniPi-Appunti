---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Coordinate Baricentriche
---
le __coordinate baricentriche__ sono un sistema per riferisci ad un punto al interno di un [[geometria - Simplex|simplex]] come una combinazione pesata dei sui componenti che lo definiscono

per il 1-[[geometria - Simplex|simplex]] ovvero per una linea si ha che 
_sia_
- $w_0,w_1$ due pesi tale che $w_0+w_1=1$
- $p_0, p_1$ i punti (0-simplex) due estremi 
allora il punto $\boldsymbol{p}$ è calcola come
$$\boldsymbol{p}=w_0\boldsymbol{p}_0+w_1\boldsymbol{p}_1$$
![[Pasted image 20240301073018.png]]


per il 2-simplex ovvero per un triangolo si ha che 
_sia_
- $w_0, w_1,w_2$ 3 pesi tale che $w_0+w_1+w_2=1$
- $p_0,p_1,p_2$ i punti (0-simplex) vertici del triangolo  
allora il punto $\boldsymbol{p}$ è calcola come
$$\boldsymbol{p}=w_0\boldsymbol{p}_0+w_1\boldsymbol{p}_1+w_2\boldsymbol{p}_2$$con $$\begin{align}{}
w_0 & =\cfrac{area(\boldsymbol{p}_1,\boldsymbol{p}_2,\boldsymbol{p})}{area(\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p}_2)} \\ \\
w_1 & =\cfrac{area(\boldsymbol{p}_0,\boldsymbol{p},\boldsymbol{p}_2)}{area(\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p}_2)} \\ \\
w_2 & =\cfrac{area(\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p})}{area(\boldsymbol{p}_0,\boldsymbol{p}_1,\boldsymbol{p}_2)} \\

\end{align}$$
![[Pasted image 20240301074317.png]]