---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture
---
le __texture__ sono array di dati che puo essere 1D, 2D o 3D, questi dati sono solitamente [[Rappresentazione delle immagini|immagini rasterizate]] ma possono rappresentare qualsiasi cosa, anche ad esempio una mappa di [[Normale di una superfice|normali]]

in una __texture__ Ogni elemento del array è chiamato __Texel__ (Texture element) e una posizione nel array è detta __texture coordinates__ oppure __UV-coordinates__ solitamente sono 2D e sono espresse con un sistema di coordinate che ha origine nel angolo in basso a sinistra i due assi sono $(u,0)$ e $(0,v)$ in modo da far corrispondere la texture ad un rettangolo tra $[0,0]$ e $[1,1]$  indicato con $[0,1]^2$![[Pasted image 20240301050343.png]]
La texture non deve essere necessariamente quadrata ma i lati devono essere potenze di due.


#### Texure Wrapping
il _texture weapping_ è la pratica di espandere il dominio delle texture da $[0,1]^2$ a $[-\infty,-\infty]\times[+\infty,+\infty]$.

Questi si puo fare con $2$ strategie alternative 
_sia_ $x$ una coordinata nel __texuture space__
_allora_ le 2 strategia sono $$\begin{array}{}
clapm(x) & = & min(max(0.0,x),1.0) \\
repeat(x) & = & x-\lfloor x\rfloor
\end{array}$$
Queste possono anche essere applicate diversamente a seconda del asse
![[Pasted image 20240301052547.png]]

nel caso di utilizzo di _repeat_ per non mostrare discontinuità c è bisogno che la texture sia __tilable__, ovvero se messe una affiano al latra queste combaciano.
 per creare questo tipo di texture si puo duplicare e fare il mirroring della texture
 ![[Pasted image 20240301053706.png]] ![[Pasted image 20240301053857.png]]