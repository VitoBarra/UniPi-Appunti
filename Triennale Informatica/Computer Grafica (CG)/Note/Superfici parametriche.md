---
Course: "[[Computer Grafica (CG)]]"
Course 2: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: "[[Superfici parametriche]]"
tags:
  - CG
---

# Superfici parametriche
---
le __[[Superfici|superfici]] parametriche__ sono un modo per [[Rappresentazione di modelli 3D|rappresentare oggetti in uno spazio 3D]] si basano sulle [[Curve parametriche|Curve parametriche]] infatti sono definite in modo simile ma il dominio ha una dimensione in piu sono definite come 
_sia_ 
- $A \subseteq \mathbb{R}^2$ un [[Insiemi Matematici|insieme]] chiamato spazio dei parametri
- $B \subseteq \mathbb{R}^3$ le coordinate dello spazio 3D
_allora_ una __superfice parametrica__ è definita da una [[Funzioni|funzione]] $S:A\to B$ tale che $$S(t,s)=(X(t,s),Y(t,s),Z(t,s))$$
E solitamente si ha che $t,s \in [0,1]$
![[Pasted image 20240223231455.png]]

#### Tensor product surface
la __Tensor product surface__ è un modo per definire le curve parametriche 
è basate sulla definizione di punti nello spazio detti __control net__ e la superfice è generata a partire da questi punti. 

per rendere la superfice piu smooth si usano delle funzioni di __blending__, dalla scelta della funzione dipendono le proprietà di [[Continuità di una funzione|continuità]], [[Funzioni differenziabili|differenziabilita]] e se la curva é  un [[Interpolazione VS approssimazione|interpolazione o una approssimazione]]  
La formulazione generale é la seguente
_sia_
- $P$ il __control polygon__ ovvero l [[Insiemi Matematici|insieme]] dei __control net__ di [[Cardinalità di un insieme|cardinalitá]]  $n \times m$ 
- $p_{ij}$ un __control net__
- $B_i(\cdot),B_j(\cdot)$ due __funzione di blending__
_allora_ vale che $$S(t,s)=\sum^n_{i=0}\sum^m_{j=0}p_{ij}B_i(t)B_j(s) \ \ \ 0 \leq t \leq 1$$