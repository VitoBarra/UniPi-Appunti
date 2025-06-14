---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: "[[Superfici parametriche]]"
---

# Superfici parametriche - Bezier patches Bicubiche
---
le __Bazier patches bicubiche__ sono [[Superfici parametriche|superfici parametriche]] che si basano sulla [[Curve parametriche - Curve di Bezier|curve di bezier]]. Sono definite come
_sia_
- $P$ il __control polygon__ ovvero l [[Insiemi Matematici|insieme]] dei __control net__ di [[Insiemi - Cardinalita|cardinalitá]]  $n \times m$ 
- $p_{ij}$ un __control net__
- $B_i(\cdot),B_j(\cdot)$ due __funzione di blending__ realizzate con il [[Polinomio di Bernstein|Polinomio di Bernstein]]
_allora_ una __Bazier patches bicubiche__ è definita come $$S(t,s)=\sum^m_{j=0}\sum^n_{i=0}p_{ij}B_i(t)B_j(s) \ \ \ 0 \leq t \leq 1$$e siccome il numero di punti rappresentabili dipendono dal grado dei polinomi usati avremmo che il numero di control net è $(n+1) \times (m+1)$ 
![[Pasted image 20240223232417.png]]

Un esempio celebre dell applicazione di queste tipo di superfici è la __Utah Teapoth__ 
![[Pasted image 20240224002507.png]]


###### Interpolazione e derivata
le __Bazier patches__ interpolano tra gli endpoint $(0,0),(0,n),(n,0),(n,n)$  
![[Pasted image 20240224001239.png]]

###### Derivata di una Patches di bezier
la [[Derivate|derivata]] di questa [[Superfici|superfice]] è la seguente $$
\begin{array}{\displaystyle}
\displaystyle\cfrac{d}{ds}S(t,s)=\sum^m_{j=0}B_{j,n}(t) \cfrac{d}{ds}\sum^n_{i=0}\boldsymbol{p}_{i,j}B_{i,n}(s) \\
\displaystyle\cfrac{d}{dt}S(t,s)=\sum^n_{i=0}B_{i,n}(s) \cfrac{d}{dt}\sum^m_{j=0}\boldsymbol{p}_{i,j}B_{j,n}(t)
\end{array}$$ 
###### Norma 
per calcolare la [[Normale di una superfice parametrica|norma]] si puo calcolare utilizzando il [[Prodotto Vettoriale (Cross product)|cross pruduct]]
$$N(t,s)=normalize\left(\cfrac{d}{ds}S(t,s)\times\cfrac{d}{dt}S(t,s)\right)$$