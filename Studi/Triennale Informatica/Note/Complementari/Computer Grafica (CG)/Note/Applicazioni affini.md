---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
  - AL
---

# Applicazioni affini
---
Le __applicazioni affini__ sono delle _[[Applicazioni Lineari|Applicazioni lineari]]_ che pero non hanno piu un _punto di origine fisso_ che è quindi libero di variare ed essere spostato per _traslazione_.

Usando le [[Coordinate omogenee|coordinate omogenee]] una __trasformazione affine__ viene espressa dalla [[Matrice|matrice]] $$\begin{bmatrix}
a_{xx} & a_{xy}   & v_{x} \\
a_{yx}  & a_{yy} & v_{y}  \\
0 & 0 & 1  
\end{bmatrix}$$dove la prima sotto matrice $2\times 2$ e rappresenta la parte _lineare_ ovvero _[[Trasformazioni Geometriche affini#Rotazioni|rotazione]]_ e _[[Trasformazioni Geometriche affini#Scaling|scaling]]_ e l ultima colonna rappresenta la parte _[[Sottospazii affini|affine]]_ ovvero la _traslazione_ del punto d origine 
![[IMG_0756.jpeg]]

Una trasformazione affine ha le seguente proprietà
1. Mantiene la _[[Vettori Collineari|colinearità]]_ dei punti, ovvero due punti se sono sulla stessa linea ci restano anche dopo la trasformazione 
2. Mantiene le _proporzioni_ ovvero presi 3 punti $p_{1},p_{2},p_{3}$ sulla stessa linea il rapporto $$\frac{\|p_{2}-p_{1}\|}{\|p_{3}-p_{1}\|}$$è preservato dopo la _trasformazione_.

![[IMG_0731.jpeg]]



> [!tip]
> questo puo essere generalizato a $n$ dimensioni aumentando il numero di righe e' colonne 



#### Matrice Inversa di trasformazioni affini
le [[Matrice|matrici]] delle __trasformazioni affine__ sono [[Matrice inversa|invertibili]] con la formula $$\begin{bmatrix}
A & v \\
0 & 1
\end{bmatrix}^{-1}=\begin{bmatrix}
  A^{-1}&-A^{-1}\boldsymbol{\mathit{v}} \\
0  & 1 
\end{bmatrix}$$ dove $A$ e la sotto matrice senza l ultima riga e l ultima colonna e $v$ il vettore __affine__, ovvero l ultima collana meno  ultimo componente. La matrice $A$ deve essere [[Matrice inversa|invertibile]]



le inverse geometricamente rappresentano l inversione del operazione, infatti abbiamo che: 
- _Traslazione_: $T_{v}^{-1}=T_{-v}$
- _Rotazioni_: $R^{-1}_{\alpha}=R_{-\alpha}$
- _Scaling_ $S^{-1}_{(s_{x},s_{y})}=S_{(1/s_{x},1/s_{y})}$

