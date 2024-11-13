---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Algoritmo di Remeshing - Loop
---
L' __[[Remeshing - Raffinamento|algoritmo di raffinamento]] Loop__ è un algoritmo classificato come __primale__ è __approssimante__ funziona solo con i  [[Poligoni|triangoli]].


Dal punto di vista combinatorio, (topologico) per ogni elementi nella [[Mesh Poligonali|mesh]] l'algoritmo segue come:
1. Per ogni faccia non fare nulla
2. Per ogni edge genera un nuovo vertice al centro del edge 
3. Per ogni vertice non fare nulla.
4. Collega i nuovi Vertici tra loro
![[Pasted image 20241111233954.png]]
Questo algoritmo ha la proprietà di trasformare una mesh di triangoli in un altra fatta di triangoli


Mentre dal punto di vista continuo l algoritmo segue come 
1.  $$ E_i = \frac{3}{8} (d_1 + d_i) + \frac{1}{8} (d_{i-1} + d_{i+1}) $$
2. $$ 
\begin{array}
\mathbf{d}'_1 = \alpha_n \mathbf{d}_1 + \frac{(1 - \alpha_n)}{n} \sum_{j=2}^{n+1} \mathbf{d}_j \\
\alpha_n = \frac{3}{8} + \left(\frac{3}{8} + \frac{1}{4} \cos \frac{2\pi}{n} \right)^2 
\end{array} 
$$
Si applicano le maschere ![[Pasted image 20241111234249.png]]
 


Un esempio è qualcosa del tipo 
![[Pasted image 20241111234324.png]]





