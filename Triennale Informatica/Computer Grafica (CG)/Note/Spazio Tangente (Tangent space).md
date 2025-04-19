---
Course 2: "[[Computer Grafica (CG)]]"
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Spazio Tangente (Tangent space)
---
il __tangent space__ è un [[Insiemi Matematici|insieme]] di [[Frames|frame di riferimento]] detti **tangent frame** definiti su tutti i punti della [[superfici|superficie]] di un oggetto, costruirlo è utile in quanto le informazioni direzionali dipendono solo dall'oggetto e non da dove è posizionato nello spazio, è quindi invariate alla traslazione  
**sia**
- $S:\mathbb{R}^2 \to \mathbb{R}^3$ una [[Superfici parametriche|superfice parametrica]] 
- $p = S(u,v)$ un punto sulla superfice 
_allora_ il __tangent frame__ $T_S$ con origine  $p$  è costruito come$$
\begin{array}{}
	\mathbf{u}_{os}= \cfrac{\partial S(u,v)}{\partial u} \\
	\mathbf{v}_{os}= \cfrac{\partial S(u,v)}{\partial v} \\
	\mathbf{n}_{os}= \mathbf{u}_{os} \times \mathbf{v}_{os}
\end{array}
$$in questo si sta costruendo un [[Frames|frame]] che ha gli assi $X$,$Y$ in un piano tangente alla superfice e l asse $Z$ che corrisponde alla [[Normale di una superfice parametrica|normale]], facendo questa operazione per tutti i punti si ottiene il __Tangent Space__ 
![[Pasted image 20240302080857.png]]
