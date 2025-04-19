---
tags:
  - CG
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic:
---

# Superfici implicite
---
Le __[[Superfici|superfici]] implicite__ si usano per [[Rappresentazione di modelli 3D|rappresentare oggetti in uno spazio 3D digitale]] 

sia  $f(\cdot,\cdot,\cdot)$ una [[Funzioni|funzione]] trivariata 
allora una superfice implicita é  una [[Insiemi Matematici|insieme]] di punti tale che $$S=\{(x,y,z)\in  \mathbb{R}^{3}\mid f(x,y,z)=0 \}$$
dove $(x,y,z)$ sono coordinate cartesiane 
$S$ é anche detto __insieme zero__ di $f$.
Questo tipo di superfici definiscono implicitamente se un punto é al interno o al sterno della superfice con il seguente criterio
1. $f(\boldsymbol{p})<0 \iff$ $\boldsymbol{p}$ interno
2. $f(\boldsymbol{p})>0 \iff$ $\boldsymbol{p}$ esterno
3. $f(\boldsymbol{p})=0 \iff$ $\boldsymbol{p}$ é sul bordo

alcuni esempi sono $f(x,y)=x^{2}+y^{2}-r^{2}$
![[Pasted image 20240221011322.png]]
e $f(x,y,z)=x^{2}+y^{2}+z^{2}-r^{2}$
![[Pasted image 20240221013012.png]]



#### Normale di superfici implicite
la [[Normale di una superfice parametrica|normale]] di una __superfice implicita__ é  

_sia_ $\boldsymbol{p}$ un punto tale che $f(\boldsymbol{p})=0$ ovvero é sulla superfice.
_allora_ la normale corrisponde alla direzione $d$ che bisogna seguire allontanandosi da $\boldsymbol{p}$ per massimizzare $f(\boldsymbol{p}+k\boldsymbol{d})$ 
per calcolare la normale si usa quindi il gradiente come $$normal(f)=\cfrac{\nabla f(\boldsymbol{p})}{\| \nabla f(\boldsymbol{p})) \|   } = 
\cfrac{\begin{bmatrix}
\cfrac{df(\boldsymbol{p})}{dx} \\
\cfrac{df(\boldsymbol{p})}{dy} \\
\cfrac{df(\boldsymbol{p})}{dz}
\end{bmatrix}}{{\| \nabla f(\boldsymbol{p})) \|}} $$

#### Operazioni booleane 
sia  $A$ e $B$ due oggetti solidi descritti con una superfice implicita.
_allora_ si possono definire le seguenti operazioni 
- complemento: $-f_A$
- intersezione: $max(f_A,f_B)$
- unione: $\min(f_A,f_B)$
- differenza: $\max(f_A,-f_B)$
![[Pasted image 20240221015821.png]]


