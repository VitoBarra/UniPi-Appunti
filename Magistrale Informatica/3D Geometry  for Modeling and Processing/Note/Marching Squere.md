---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Marching Squere
---
il __marching Squere__ è un **[[Algoritmi|algoritmo]]** per trasformare un [[Superfici implicite|rappresentazione implicita]] (campo salare) 2D in una [[Mesh Poligonali|mesh poligonale]].

**sia** $f(x,y)$ un campo scalare che vari linearmente
si parte da dei campioni regolari di $f(x,y)$
ogni campione $(x,y)$ viene connesso in modo da formare una griglia.
![[Pasted image 20240224041830.png]]
Grazie al fatto che il campo varia linearmente abbiamo che il campo scalare puo essere calcolato in tutti i punti [[Interpolazione Bilineare|interpolando bilinearmente]] i 4 vertici della cella che contiene il punto di cui si vuole conoscere il valore. 

il __marching square__ dal campionamento vuole trovare l' [[Superfici implicite|isosuperfice]]  $\alpha$  quindi $$S=\{(x,y) \in  \mathbb{R} \mid f(x,y) =\alpha\}$$e per fare ciò si marcano i nodi in
- rosso se $f(x,y)<\alpha$
- blue se $f(x,y)>\alpha$
![[Pasted image 20240224034100.png]]
e poi
1. per ogni cella della griglia trova l intersezione con la isosurface
2. definisce un insieme per ogni permutazione di nodi blu e rossi 
per calcolare l intersezione si puo usare l [[Interpolazione Lineare|interpolazione lineare]] tra un nodo rosso $R$ e un nodo blu $B$, Possiamo dire che $$\exists t \mid  f(R)(1-t)+f(B)t = \alpha \implies  t=\cfrac{\alpha-f(R)}{f(B)-f(R)}

$$e sostituendo nella formula del [[Interpolazione Lineare|interpolazione lineare]] otteniamo l'intersezione$$p(R)(1-t)+p(R)t=\mathcal{p}$$ dove $p$ indica le coordinate in modo che $f(\mathcal{p})=\alpha$
![[Pasted image 20240224034049.png]]
utilizzando il set di $2^4=16$ [[Combinatoria|permutazioni]] e salvandoli una volta in una __look-up table__  
![[Pasted image 20240224034011.png]]
si ottiene ad esempio la superfice.
![[Pasted image 20240224034027.png]]
il **marching squares** ha un **caso ambiguo** ed è quello in cui solo 2 vertici opposti sono attivi.
con questa configurazione ci sono $4$ intersezioni con la cella e per costruzione si sa che i vertici attivi sono interni alla superfice.
Non è pero chiaro come connettere i punti di intersezione.
![[IMG- Marching squere ambiguita.png]]
Per risolvere l'ambiguità si valuta il valore del campo al centro usando l'[[interpolazione bilineare|interpolazione bilineare]] della cella e si ha che a seconda del valore nel centro
- se $> \alpha$ allora i due vertici saranno connessi da un tunnel 
- se $< \alpha$ allora i due vertici saranno separati da un conca
![[IMG - Marching cube sadle point.png]]