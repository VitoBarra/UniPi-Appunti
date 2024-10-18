---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: "[[Immage Processing]]"
topic: "[[Filtering]]"
SubTopic:
---

# Filtering - Gaussian Blur
---
il __Blur gaussiano__ è un applicazione del __[[Filtering|filtering]]__ e serve a dare un effetto di blur alle immagini in modo da ammorbidirle. questo si fa usando la [[Variabili Aleatorie Notevoli - Gaussiane|distribuzioni gaussiane]] $$f(x)=\cfrac{1}{\sigma \sqrt{ 2\pi }}e^{-\cfrac{(x-\mu)^2}{\sigma^2}}$$
![[Pasted image 20240309181916.png]]
e infatti i pesi del kernel sono assegnati con due [[Variabili Aleatorie Notevoli - Gaussiane|distribuzioni gaussiane]] con la formula
$$k(x,y)=f(x)f(y)=\cfrac{1}{\sigma^22\pi}e^{-\cfrac{(x^2+y^2)}{\sigma^2}}$$
e la formula risultate è $$Blur(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}\sum^{M}_{y=-M}f(x+N)f(y+M)I(x_0+x,y_0+y)$$è questa puo anche essere rappresentata come [[Matrici|matrice]]
![[Pasted image 20240309182711.png]]
essendo questa formula prodotto di due funzioni si puo fare un ottimizzazione  portando fuori cui che dipende solo dalla sommatoria esterna e quindi  $$Blur(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}f(x+N)\sum^{M}_{y=-M}f(y+M)I(x_0+x,y_0+y)$$in questo modo le operazioni da fare passano da $(N+M+1)^2$ a $2(N+M+1)$