---
tags:
  - CG
Subject: "[[Computer Grafica (CG)]]"
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
3. $f(\boldsymbol{p})=0 \iff$ $\boldsymbol{p}$ é

alcuni esempi sono $f(x,y)=x^{2}+y^{2}-r^{2}$
![[Pasted image 20240221011322.png]]
e $f(x,y,z)=x^{2}+y^{2}+z^{2}-r^{2}$
![[Pasted image 20240221013012.png]]



#### Normale di superfici implicite
la [[Normale di una superfice|normale]] di una superfice é  

_sia_ $\boldsymbol{p}$ un punto tale che $f(\boldsymbol{p})=0$ ovvero é sulla superfice.
_allora_ la direzione $d$ che bisogna seguire allontanandosi da $\boldsymbol{p}$ per massimizzare $f(\boldsymbol{p}+k\boldsymbol{d})$ 
per calcolare la normale si usa qundi il gradiente come $$normal(f)=\cfrac{\nabla f(\boldsymbol{p})}{\| \nabla f(\boldsymbol{p})) \|   } = \begin{bmatrix}
\cfrac{d}{dx}f(\boldsymbol{p}) \\
\cfrac{d}{dy}f(\boldsymbol{p}) \\
\cfrac{d}{dz}f(\boldsymbol{p})
\end{bmatrix} $$

#### Operazioni booleane 
sia  $A$ e $B$ due oggetti solidi descritti con una superfice implicita.
_allora_ si possono definire le seguenti operazioni 
- complemento: $-f_A$
- intersezione: $max(f_A,f_B)$
- unione: $\min(f_A,f_B)$
- differenza: $\max(f_A,-f_B)$
![[Pasted image 20240221015821.png]]


#### Metaballs
una delle applicazione delle superfici implicite sono le metaball.

Sono sfere che se lontane appaiano come sfere indivuali ma che se avvvicinate iniziano ad unirsi
![[Pasted image 20240221020420.png]]

![[Pasted image 20240221020437.png]]
![[Pasted image 20240221020446.png]]


per definire questo tipo di superfici si parete definendo la funzione $f$ come una somma di funzioni semplici e quindi si avrà $$f(x)=\sum_if_i(x)$$ dove ogni funzione $f_i(x)$ é definita come $$f_i(x)=\begin{cases}
1-\cfrac{r^{2}}{R^{2}}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$ con $r=\| x-x_i \|$ e dove $R$ é un raggio di supporto e al di fuori di questo l influenza di $f_i(x)$ é 0
$f_i$ dipende solo dalla distanza da un punto 3D $x_i$
![[Pasted image 20240221021044.png]]
L _isovalue_ $\alpha$ é un valore tra $0$ e $1$ che definisce la isosurface

 va anche scelta bene la funzione $f_i$ da usare infatti la funzione $$f_i(x)=\begin{cases}
1-\cfrac{r^{2}}{R^{2}}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$ non é  una buona funzione siccome ha derivata [[Derivate|discontinua]]
![[Pasted image 20240221021602.png]]
una miglire é $$f_i(x)=\begin{cases}
2\cfrac{r^3}{R^3} -3\cfrac{r^2}{R^2}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$
![[Pasted image 20240221021730.png]]

![[Pasted image 20240221021843.png]]