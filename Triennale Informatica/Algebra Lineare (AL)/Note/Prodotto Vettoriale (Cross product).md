---
Course: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---
# Prodotto Vettoriale (Cross product)
---
Il prodotto vettoriale è un'[[Operazioni algebriche|operazione]] che combina _due vettori_ per produrre un _terzo vettore_, [[Vettori Ortogonali|ortogonale]] al _piano_ formato dai primi due.
il _prodotto vettoriale_ è definito solo in con vettori a 3 componenti.
Il prodotto vettoriale tra due vettori  $\boldsymbol{a}$  e  $\boldsymbol{b}$ è indicato come $\boldsymbol{a} \times \boldsymbol{b}$ 
_siano_ $\boldsymbol{a} = (a_x, a_y, a_z)$ e $\boldsymbol{b} = (b_x, b_y, b_z)$  i due vettori 
_allora_$$\mathbf{a} \times \mathbf{b} =\begin{bmatrix} 
a_yb_z - b_ya_z\\ 
-a_xb_z + b_xa_z\\
a_xb_y - b_xa_y
\end{bmatrix}$$ per ricordarlo esiste la regola mnemonica che consiste nel calcolare il determinante della matrice $$\det \left(\begin{bmatrix}
\boldsymbol{i} & \boldsymbol{j} & \boldsymbol{k} \\
a_{x} & a_{y} & a_{z} \\
b_{x} & b_{y} & b_{z}
\end{bmatrix}\right)=\boldsymbol{i}(a_{y}b_{z}-b_{y}a_{z})-\boldsymbol{j}(a_{x}b_{z}-b_{x}a_{z})+\boldsymbol{k}(a_{x}b_{y}-b_{x}a_{y})$$
##### Proprietà algebriche
è [[Proprietà del operazioni-Anticommutatività|Anticomutativa]] ovvero vale $$\boldsymbol{a} \times \boldsymbol{b}=-(\boldsymbol{b} \times \boldsymbol{a})$$
![[IMG_0790.jpeg]]
ed è _distributiva_ sulla somma $$\boldsymbol{a} \times(\boldsymbol{b}+\boldsymbol{c})=\boldsymbol{a} \times \boldsymbol{c}+\boldsymbol{a}\times \boldsymbol{b}$$
##### Proprietà geometriche
la [[Norme Matriciali e Norme Vettoriali|norma]] (euclidea) del _prodotto vettoriale_ vale$$\|\boldsymbol{a}\times \boldsymbol{b}\|=\|\boldsymbol{a}\|\| \boldsymbol{b}\|\sin(\theta)$$  che equivale al area del _paralelogramma_ $$\boldsymbol{p},\boldsymbol{p}+\boldsymbol{a},\boldsymbol{p}+\boldsymbol{a}+\boldsymbol{b},\boldsymbol{p}+\boldsymbol{b}$$
![[IMG_0791.jpeg]]
che significa che l area del triangolo $\boldsymbol{p}_{0},\boldsymbol{p}_{1},\boldsymbol{p}_{2}$ può essere calcolata come $$\|(\boldsymbol{p}_{1}-\boldsymbol{p}_{0})\times (\boldsymbol{p}_{2}-\boldsymbol{p}_{0})\|=2area(\boldsymbol{p}_{1},\boldsymbol{p}_{2},\boldsymbol{p}_{3})$$![[IMG_0792.jpeg]]




### Cross Pruduct 2D
il coss pruduct 2D è un [[Prodotto Scalare|prodotto scalere]] e vale che $$\begin{bmatrix}
a \\b
\end{bmatrix} \times \begin{bmatrix}
c \\d
\end{bmatrix} = ad -cd$$