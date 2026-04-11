---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
Area: 
topic: 
SubTopic:
---

# Interpolazione Tri-lineare
---
L'**interpolazione trilineare** è un metodo che stima il valore di una funzione in uno spazio tridimensionale tra otto punti noti, utilizzando una [[Rette|combinazione di rette]] che _congiungono_ i valori lungo ogni dimensione.  
Questo approccio estende l'[[Interpolazione Lineare|interpolazione lineare]] al caso tridimensionale, fornendo una stima continua e lineare del valore della funzione all'interno di un cubo.

_siano_ otto coordinate corrispondenti ai vertici di un cubo:
$$(x_0, y_0, z_0),\ (x_1, y_0, z_0),\ (x_0, y_1, z_0),\ (x_1, y_1, z_0),\ (x_0, y_0, z_1),\ (x_1, y_0, z_1),\ (x_0, y_1, z_1),\ (x_1, y_1, z_1)$$
e i loro rispettivi valori della funzione:
$$(f_{000},\ f_{100},\ f_{010},\ f_{110},\ f_{001},\ f_{101},\ f_{011},\ f_{111})$$

_allora_ la formula per l'_interpolazione tri-lineare_ è data da:$$
f(x,y,z) = \sum_{i=0}^1 \sum_{j=0}^1 \sum_{k=0}^1 f_{ijk} \cdot (1 - i - (-1)^i t_x) \cdot (1 - j - (-1)^j t_y) \cdot (1 - k - (-1)^k t_z)
$$dove:
- $f(x,y,z)$ è il _valore interpolato_,
- $(x,y,z)$ è il punto tridimensionale in cui si desidera stimare il valore,
- $t_x = \frac{x-x_0}{x_1-x_0}$ è la posizione normalizzata lungo $x$,
- $t_y = \frac{y-y_0}{y_1-y_0}$ è la posizione normalizzata lungo $y$,
- $t_z = \frac{z-z_0}{z_1-z_0}$ è la posizione normalizzata lungo $z$,
- $f_{ijk}$ sono i valori della funzione nei vertici del cubo.

In pratica, si eseguono tre [[Interpolazione Lineare|interpolazioni lineari]] sui lati, poi due interpolazioni sui piani, e infine un'ultima interpolazione tra i due piani ottenuti.





o equivalentemente come 
$$
T(x,y,z) = axyz + bxy + cyz + dxz + ex + fy + gz + h
$$

$$
\begin{aligned}
a &= v1 + v3 + v4 + v6 - v0 - v7 - v5 - v2 \\
b &= v0 + v2 - v1 - v3 \\
c &= v0 + v7 - v4 - v3 \\
d &= v0 + v5 - v1 - v4 \\
e &= v1 - v0 \\
f &= v3 - v0 \\
g &= v4
\end{aligned}
$$
![[IMG - cube index value.png]]

