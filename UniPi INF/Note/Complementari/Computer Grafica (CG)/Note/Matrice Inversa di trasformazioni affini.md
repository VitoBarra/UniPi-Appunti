---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Matrice Inversa di trasformazioni affini
---
le [[Matrice|matrici]] delle [[Trasformazioni affini|trasformazioni affine]] sono facilmente [[Matrice inversa|invertibili]] e si calcolano come $$\begin{bmatrix}
A & v \\
0 & 1
\end{bmatrix}^{-1}=\begin{bmatrix}
  A^{-1}&-A^{-1}\boldsymbol{\mathit{v}} \\
0  & 1 
\end{bmatrix}$$
le inverse geometricamente rapresentano l inversione del operazione, infatti abbiamo che: 
- _traslazione_: $T_{v}^{-1}=T_{-v}$
- _rotazioni_: $R^{-1}_{\alpha}=R_{-\alpha}$
- _scaling_ $S^{-1}_{(s_{x},s_{y})}=S_{(1/s_{x},1/s_{y})}$

##### Esempio
essendo la [[Trasformazioni affini|matrice di rotazione]] [[Ortogonalità E Ortonormalità|ortonormale]] e la [[Matrice inversa|matrice inversa]] si calcola come $$\begin{bmatrix}
R & \boldsymbol{c} \\
0 & 1
\end{bmatrix}^{-1}=\begin{bmatrix}
R^{T} & -R^{T}c \\
0 & 1
\end{bmatrix}$$
