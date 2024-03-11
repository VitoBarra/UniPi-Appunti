---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Immage Processing]]"
SubTopic:
---

# Filtering
---
il filter è una pratica del [[Immage Processing|immage processing]]. Applicare un __Filtro__ ad un immagine consiste nel sostituire ogni pixel con una somma pesata dei pixel suoi vicini.
Questi pixel vengono selezionati e pesati con una [[Matrice|matrice]] di pesi solitamente [[Matrici quadrate|quadrata]] chiamata __filtering kernel__ $K$  è detta __dimensione del kernel__ 
![[Pasted image 20240308171458.png]]

_sia_ 
- $F$ il filtro rappresentato dal __kernel__
- $I$ l immagine originale
- $I'$ l immagine filtrata 
- $N$ il raggio del filtro orizzontale
- $M$ il raggio del filtro verticale 
- $T$ è la somma dei pesi
_allora_ sia ha che la formula completa di filtro è $$I'(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}\sum^{M}_{y=-M}F(x+N,y+M)I(x_0+x,y_0+y)$$ e questa coincide con la [[Formule della convoluzione|formula di convoluzione]]  $\cfrac{1}{T}$ è un termine di normalizzazione
e i pixel coinvolti per ogni passo sono $(2N+1)(2M+1)= 4NM+2(N+M)+1$ e siccome solitamente i kernel sono quadrati si ha che $N=M$  
![[Pasted image 20240308170039.png]]

#### Operatore Sobel
l __operatore sobel__ è un applicazione del __filtering__ e serve a derivare un imagine sul asse $x$ o $y$. L effetto finale e che i bordi orizonatli ($x$) o verticali ($y$) appaiano di piu 
![[Pasted image 20240308162012.png]]
![[Pasted image 20240309181559.png]]


#### Gaussian Blur
il __Blur gaussiano__ è un applicazione del __filtering__ e serve a dare un effetto di blur alle immagini in modo da ammorbidirle. questo si fa usando la [[Variabili Aleatorie Notevoli - Gaussiane|distribuzioni gaussiane]] $$f(x)=\cfrac{1}{\sigma \sqrt{ 2\pi }}e^{-\cfrac{(x-\mu)^2}{\sigma^2}}$$
![[Pasted image 20240309181916.png]]
e infatti i pesi del kernel sono assegnati con due [[Variabili Aleatorie Notevoli - Gaussiane|distribuzioni gaussiane]] con la formula
$$k(x,y)=f(x)f(y)=\cfrac{1}{\sigma^22\pi}e^{-\cfrac{(x^2+y^2)}{\sigma^2}}$$
e la formula risultate è $$Blur(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}\sum^{M}_{y=-M}f(x+N)f(y+M)I(x_0+x,y_0+y)$$è questa puo anche essere rappresentata come [[Matrice|matrice]]
![[Pasted image 20240309182711.png]]
essendo questa formula prodotto di due funzioni si puo fare un ottimizzazione  portando fuori cui che dipende solo dalla sommatoria esterna e quindi  $$Blur(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}f(x+N)\sum^{M}_{y=-M}f(y+M)I(x_0+x,y_0+y)$$in questo modo le operazioni da fare passano da $(N+M+1)^2$ a $2(N+M+1)$