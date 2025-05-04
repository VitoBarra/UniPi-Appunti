---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione sfera proiezione ortogonale
---
Un esempio classico di **[[Parametrizzazione|parametrizzazione]]** è quello della semisfera definita da $S=x^2 + y^2 + z^2 = 1$, dove il dominio $\Omega$ è il disco di raggio 1 nel piano $uv$ :
![[IMG - parametrizazione proiezione ortogonale.png]]
Nel caso di **proiezione ortografica**, dove $$
\begin{array}{}
f^{-1}(x, y, z)  & = &  (x, y)\\
f(u,v)  & = &  (u, v, \sqrt{1 - u^2 - v^2})
\end{array}
$$dove la terza coordinata è dedotta dal [[teorema di pitagora|teorema di Pitagora]].
