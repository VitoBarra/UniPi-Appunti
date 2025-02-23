---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: "[[Immage Processing]]"
topic: 
SubTopic:
---

# Filtering
---
il __filtering__ è una pratica del [[Immage Processing|immage processing]]. Applicare un __Filtro__ ad un immagine consiste nel sostituire ogni pixel con una somma pesata dei pixel suoi vicini.
Questi pixel vengono selezionati e pesati con una [[Matrici|matrice]] di pesi solitamente [[Matrici quadrate|quadrata]] chiamata __filtering kernel__ $K$  è detta __dimensione del kernel__ 
![[Pasted image 20240308171458.png]]

_sia_ 
- $F$ il filtro rappresentato dal __kernel__
- $I$ l immagine originale
- $I'$ l immagine filtrata 
- $N$ il raggio del filtro orizzontale
- $M$ il raggio del filtro verticale 
- $T$ è la somma dei pesi
_allora_ sia ha che la formula completa di filtro è $$I'(x_0,y_0)=\cfrac{1}{T}\sum^{N}_{x=-N}\sum^{M}_{y=-M}F(x+N,y+M)I(x_0+x,y_0+y)$$ e questa coincide con la [[Operazione di convoluzione|formula di convoluzione]]  $\cfrac{1}{T}$ è un termine di normalizzazione
e i pixel coinvolti per ogni passo sono $(2N+1)(2M+1)= 4NM+2(N+M)+1$ e siccome solitamente i kernel sono quadrati si ha che $N=M$  
![[Pasted image 20240308170039.png]]

#### Operatore Sobel
l __operatore sobel__ è un applicazione del __filtering__ e serve a derivare un immagine sul asse $x$ o $y$. L effetto finale e che i bordi orizzontali ($x$) o verticali ($y$) appaiano di piu 
![[Pasted image 20240308162012.png]]
![[Pasted image 20240309181559.png]]

