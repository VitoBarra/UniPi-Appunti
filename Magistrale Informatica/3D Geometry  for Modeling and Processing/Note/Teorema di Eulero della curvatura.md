---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Teorema di Eulero della curvatura
---
il **Teorema di Eulero** dice che:
**sia** $S$  una  [[Curve parametriche|superfice parametriche]] smooth.
**allora** per ogni $x \in S$ per cui si puo definire la [[Curvatura di una superfice|curvatura]] esistono due **direzioni principali**
- $\mathbf{t}_M$ : la direzione per cui la [[Curvatura di una superfice|curvatura]] è **massima**
- $\mathbf{t}_m$:  la direzione per cui la [[Curvatura di una superfice|curvatura]] è **minima**
 **se** $t_M\not=t_m$  ovvero non siamo in casi in cui la curvatura è banale (come ad esempio una sfera)
**allora** vale che $t_M$  e $t_m$ sono  [[Vettori Ortogonali|Ortogonali]] tra loro
vale anche che per una qualsiasi direzione $t$ questa forma un angolo $\theta$ con la direzione $\mathbf{t}_M$ e vale che la curvatura in quella direzione è $$
\kappa_t = \kappa_1 \cos^2 \theta + \kappa_2 \sin^2 \theta $$Questa relazione permette di calcolare la curvatura in qualunque direzione a partire dalle sole **curvature principali**
![[IMG - Teorema di Eulero della curvatura.png]]