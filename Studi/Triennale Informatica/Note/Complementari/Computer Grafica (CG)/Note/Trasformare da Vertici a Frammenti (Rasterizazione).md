---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Trasformare da Vertici a Frammenti (Rasterizazione)
---
Il Processo di trasformazione da geometria in pixel (Rasterizazione) avviene fatto sulla __View Port__ ovvero dopo che la geometria in __[[Proiettare una scena 3D in 2D#World Space|word space]]__ viene mappata sul View Port,
quindi questo processo avviene dopo che la geometria viene [[Proiettare una scena 3D in 2D|proiettata sullo schermo]] 

Siccome la __View Port__ ha Coordinate _discrete_ si pone il problema di scegliere quali frammenti della geometria (che e' espressa in spazzi continui) devono essere effettivamente disegnati sulla __View Port__


Questo processo e' detto di "Rasterizazione" delle [[Computer grafica - Primitive algebriche|primitive geometriche]]
### Rasterizazione delle primitive
Rasterizazione dei punti
![[IMG_0784.jpeg]]

Rasterizazione delle _linee_
l Algoritmo di _renderizzazione_ di una linea passante da due punti dipende dallo _slope_ della [[Retta|retta]] ovvero dal suo _coefficiente angolare_ calcolato come$$m=\frac{y_{1}-y_{0}}{x_{1}-x_{0}}$$
e vale che $$\begin{cases} 
\begin{cases}
y=y_{0}+m(x-x_{0})  \\
x =x+1
\end{cases} & if & m \in  [-1,1]\\
\begin{cases}
x=x_{0}+\frac{1}{m}(y-y_{0})\\
y=y+1
\end{cases} & else
\end{cases}$$dove gli $=$ sono assegnamenti. 
L algoritmo garantisce che  tutti i pixel della _linea_ sono _adiacenti_
![[IMG_0783.jpeg]]
![[IMG_0782.jpeg]]


[[Eliminazione di Superfici non visibili]]