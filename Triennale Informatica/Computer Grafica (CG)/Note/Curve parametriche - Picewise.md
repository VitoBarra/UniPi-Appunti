---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Curve parametriche - Picewise
---
le __curve parametriche picewise__  un tipo di [[Curve parametriche|curve parametriche]] sono definite da una concatenazione di segmenti definita da una sequenza di equazioni che [[Interpolazione Lineare|interpolano linearmente]] tra un punto al altro, il modo di interpolare é completamente arbitrario e dipende dai range e dalle equazioni, si possono quindi creare segmenti dove l interpolazione é piu veloce o piu lenta.$$f(t)=\begin{cases}
eq_{1} & t\in  [a_0,a_1]\\ 
eq_{2} & t\in  [a_1,a_2] \\ 
 & \vdots \\ 
eq_{n} & t\in  [a_{n-1},a_n]
\end{cases}$$ 
![[Pasted image 20240222173959.png]]