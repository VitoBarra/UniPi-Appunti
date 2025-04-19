---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Curvatura di una superfice
---
la **curvatura di una superfice** 3D indica **quanto rapidamente cambia l’angolo di salita o discesa** della superfice anche vista come [[Derivate|derivata]] della [[Derivate|derivata]] di una superfice

Per definire la **curvatura di una superficie** 3D  indicata con $k$ si ridurre localmente il problema a un contesto 2D.
**sia**
- $S(u,v)$ una [[Superfici parametriche|superfice parametrica]]
- $p \in S(u,v)$ un punto sulla  
- $\mathbf{n}_p$ la [[Normale di una superfice parametrica|normale]] di $S$ nel punto $p$
- $\mathbf{x}_u,\mathbf{x}_v$ due vettori appartenenti allo [[Spazio Tangente (Tangent space)|spazio tangente]] con origine $p$ 
allora si puo definire un [[Vettori|vettore]] $t$  parametrizzato nel angolo $\varphi$ che indica una direzione$$ t(\varphi)= \cos\varphi \frac{x_u}{\|x_u\|} + \sin\varphi \frac{x_v}{\|x_v\|}$$prendo l'insieme di tutte de direzioni si ottiene un cerchio intorno a $p$ 
![[IMG - vettore tangente ad una superfice.png]]
generando un piano $P$ che passa per $t(\varphi)$ e $n_p$  e prendendo l'intersezione tra $P$ e $S$   si ha una curva 2D indicata con $c$  
![[IMG - intersezone tra vettore tangente e normale.png]]
sulla curva $c$ si puo calcolare direttamente la [[Derivate|derivata]] seconda ovvero la curvatura di $c$ e ottenendo la **curvatura della superfice originale** nella direzione $t$, rispetto al punto $p$. ripentendo questo per ogni punto sulla superfice è ogni direzione si ottiene la **curvatura** globale della superfice.




#### Curvatura 2D con cerchio osculate
un modo per definire la curvatura in 2D oltre alla derivata [[Derivate|seconda]] della curva stessa è tramite il **cerchio osculante**. 

**sia** $C$ una [[Funzioni|funzione]] (curva) e si vuole calcolare la curvatura in $p$ allora
Il **cerchio osculante** di raggio $r$ è un cerchio che ha la stessa [[Retta tangente|tangente]] e **curvatura** del punto $p$  su $C$  
allora si puo definire la curvatura di $p$ come  $k= \cfrac{1}{r}$
![[IMG - cerchio osculante.png]]
Se la curva in quel tratto è perfettamente dritta, il tasso di variazione della [[Derivate|derivata]] prima è nullo si avrà il raggio del cerchio osculante tende a infinito $r = \infty$, quindi la conseguentemente la curvatura è nulla: $k = \cfrac{1}{\infty} = 0$

All’opposto, più una curva è “stretta”, più il cerchio osculante è piccolo, più il raggio tende a zero $r\to 0$  e la curvatura aumenta, al limite si ha una angolo a $90\degree$ gradi dove$$
r \to 0 \quad \Rightarrow \quad k \to \infty
$$


Il **segno della curvatura** può essere interpretato geometricamente infatti il segno indica in che lato della curva si trova il centro del cerchio, e lo si puo interpretare con la concavità o convessità.

