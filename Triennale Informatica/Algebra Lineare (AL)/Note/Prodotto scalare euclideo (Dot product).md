---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Prodotto scalare Euclideo (Dot product)
---
Il __prodotto scalare euclideo__ anche chiamato __dot product__ è tipo di [[Prodotto Scalare|Prodotto Scalare]]
_siano_ $\boldsymbol{x},\boldsymbol{y}$ due vettori di dimensione $n$
_allora_ il _prodotto scalare euclideo_ è definito come$$
\langle x,y\rangle = x^{T} \cdot y
=\begin{bmatrix}
x_1 & \dots & x_n 
\end{bmatrix}\cdot
\begin{bmatrix}
y_1 \\
\vdots \\
y_n
\end{bmatrix}=\sum_{i=0}^{n}x_{i}y_{i}$$
dove $\cdot$ è il  [[Prodotto tra matrici|prodotto tra matrici]]


#### Geometricamente
per il _prodotto scalare euclideo_ vale che $$\boldsymbol{a}\cdot \boldsymbol{b}=\|\boldsymbol{a}\|\|\boldsymbol{b}\|\cos \theta$$
dove $\|\cdot\|$ è la [[Norme Matriciali e Norme Vettoriali|norma euclidea]] 
questa formula ci da la possibilità di calcolare l _l’angolo_ tra i due vettori $$\theta=\arccos \left( \frac{\boldsymbol{a} \cdot \boldsymbol{b}}{\|\boldsymbol{a}\|\|\boldsymbol{b}\|} \right)$$
e la lunghezza della [[Applicazione lineare - Proiezione|proiezione]] [[Vettori Ortogonali|ortogonale]] $$\boldsymbol{b}\cdot \frac{\boldsymbol{a}}{\|\boldsymbol{a}\|}$$![[IMG_0787.jpeg]]
il _prodotto scalare euclideo_ è _massimo_ per vettori [[Rette Parallele|paralleli]] $$\theta=0 \implies \boldsymbol{a} \cdot \boldsymbol{b}=\|\boldsymbol{a}\|\|\boldsymbol{b}\|$$![[IMG_0788.jpeg]]
mentre è _minimo_ per vettori _anti paralleli_ $$\theta=\pi \implies \boldsymbol{a} \cdot \boldsymbol{b}=-\|\boldsymbol{a}\|\|\boldsymbol{b}\|$$![[IMG_0789.jpeg]]
