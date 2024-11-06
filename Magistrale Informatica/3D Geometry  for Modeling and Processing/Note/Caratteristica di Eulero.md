---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Caratteristica di Eulero
---
__sia__
- $\Sigma$ un $k$-[[Complesso simpliciale|complesso simpliciale]]
- $\sigma_d$ l insieme dei simplessi $\sigma \in \Sigma$ di dimensione $d$
__allora__ la __Caratteristica di Eulero__ è definita come $$\chi=\sum_{d=0}^k (-1)^d |\sigma_d|$$In particolare è importante per il caso dei $2$-[[Complesso simpliciale|complesso simpliciale]] e si ha che la __caratteristica di Eulero__ è definita come  
$$\chi=V - E + F$$
questo valore è costante indipendentemente dalle modifiche locali che si fanno al __[[Complesso simpliciale|complesso simpliciale]]__ al patto che il nuovo complesso sia anche esse corretto e [[Complesso simpliciale#Complesso simpliciale massimale|massimo]] 
![[Pasted image 20241027004649.png]]

La __caratteristica di Eulero__ puo anche essere messa in relazione al [[Genus|genus]] infatti si ha che $$\chi =2-2g-b$$dove $b$ è definito come __loop di edge__ sul bordo e serve a gestire i casi di [[Superfici|superfici]] aperte. 
Il fatto che questo funzioni puo essere dimostrato visivamente, infatti ogni __loop di edge del bordo__  può essere chiuso aggiungendo un __vertice__ e un edge per vertice del bordo che si vuole chiedere. In questo modo il [[Complesso simpliciale|complesso simpliciale]] tappato avrà esattamente un vertice in più rispetto al complesso di prima e $k$ nuove facce e vertici. 
![[Pasted image 20241027011544.png]]
in questo modo tappando $b$ buchi aggiungendo quindi $b$ vertici si ottiene una nuovo [[Complesso simpliciale|complesso simpliciale]]  $A'$ è la sua __caratteristica di Eulero__ pari a $$
\begin{flalign}{}
\chi' &= \chi + (V-V') -(E-E') + (F-F')  \\
      &= \chi + b \cancel{– k} \cancel{+ k} \\
      &= \chi +b
\end{flalign}$$e da qui si puo ottenere quella origina spostando i termini $$\chi=\chi'-b$$


