---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---


# Algoritmo di Remeshing - Butterfly
---
L' __[[Remeshing - Raffinamento|algoritmo di raffinamento]] Butterfly__ è un algoritmo classificato __primale__ è __Interpolante__ funziona solo con i [[Poligoni|triangoli]].



Dal punto di vista combinatorio, (topologico) per ogni elementi nella [[Mesh Poligonali|mesh]] l'algoritmo segue come:
1. Per ogni faccia aggiungi un vertice al centro
2. Per ogni edge genera un nuovo vertice al centro del edge 
3. Per ogni vertice non fare nulla.
4. Collega i nuovi Vertici tra loro
![[Pasted image 20241111235706.png]]




Mentre dal punto di vista continuo l algoritmo segue come 
1.  $$ E_1 = \frac{1}{2} ( \mathbf{d}_1 + \mathbf{d}_2 ) + \omega ( \mathbf{d}_3 + \mathbf{d}_4 ) - \frac{\omega}{2} ( \mathbf{d}_5 + \mathbf{d}_6 + \mathbf{d}_7 + \mathbf{d}_8 ) $$
2.  $$ \mathbf{d}'_i = \mathbf{d}_i $$


questo algoritmo con altri che sono interpolanti soffrono del fenomeno di ringing ovvero tra un iterazione è l'altra si generano delle oscillazioni che fanno perdere il senso originale della mesh.
![[Pasted image 20241111235804.png]]
Mentre funziona bene per geometrie molto curve ad esempio un toro.



