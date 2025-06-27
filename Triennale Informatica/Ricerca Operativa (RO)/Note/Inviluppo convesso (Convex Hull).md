---
Course: "[[Ricerca Operativa (RO)]]"
Course 2: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
  - RO
Area: 
topic: 
SubTopic:
---

# inviluppo convesso (Convex Hull)
---
L’__inviluppo convesso__ di un [[Insiemi Matematici|insieme]] $S \subset \mathbb{R}^n$ finito, denotato con $CH(K)$ , è definito dall’insieme di tutte le [[Convessita|combinazioni convesse]] di tutti i punti di $K$.
![[IMG - inviluppo convesso di un triangolo.png]]

un altra **definizione equivalente** è la seguente:
**sia** $EH_i(S)$ un [[Semispazio|Semispazio]] definito da una [[rette|retta passante]] per un punto $S$ e che non contiene nessun punto di $S$.  
**allora** l **inviluppo convesso** è definito come $$CH(K) = \mathbb{R}^n \backslash \bigcup_i EH_i(S)$$![[IMG - Inviluppo convesso (Convex Hull) con sempispazi.png]]

