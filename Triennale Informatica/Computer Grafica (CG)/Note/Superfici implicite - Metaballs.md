---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Superfici implicite - Metaballs
---
le **metaball** sono un applicazione delle [[superfici implicite|superfici implicite]]. Sono sfere che se lontane appaiano come sfere individuali ma che se avicinate iniziano ad unirsi
![[IMG - Superfici implicite - Metaballs 1.png]]

![[IMG - Superfici implicite - Metaballs 2.png]]
![[IMG - Superfici implicite - Metaballs 3.png]]

per definire questo tipo di superfici si parete definendo la funzione $f$ come una somma di funzioni semplici e quindi si avrà $$f(x)=\sum_if_i(x)$$ dove ogni funzione $f_i(x)$ é definita come $$f_i(x)=\begin{cases}
1-\cfrac{r^{2}}{R^{2}}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$ con $r=\| x-x_i \|$ e dove $R$ é un raggio di supporto e al di fuori di questo l influenza di $f_i(x)$ é 0
$f_i$ dipende solo dalla distanza da un punto 3D $x_i$
![[IMG - Superfici implicite - Metaballs 4.png]]
L _isovalue_ $\alpha$ é un valore tra $0$ e $1$ che definisce la isosurface

 va anche scelta bene la funzione $f_i$ da usare infatti la funzione $$f_i(x)=\begin{cases}
1-\cfrac{r^{2}}{R^{2}}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$ non é  una buona funzione siccome ha derivata [[Derivate|discontinua]]
![[IMG - Superfici implicite - Metaballs 5.png]]
una miglire é $$f_i(x)=\begin{cases}
2\cfrac{r^3}{R^3} -3\cfrac{r^2}{R^2}  & if  & r<R \\
0 & if  & r \geq R 
\end{cases}$$
![[IMG - Superfici implicite - Metaballs 6.png]]

![[IMG - Superfici implicite - Metaballs 7.png]]