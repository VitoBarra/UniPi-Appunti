---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Marching cube
---
si puo usare il __marching cube__ per trasformare un campo salare in una [[Mesh Poligonali|mesh poligonale]].

sia $f(x,y)$ un campo scalare
si parte da dei campioni regolari di $f(x,y)$
ogni campione $(x,y)$ viene connesso in modo da formare una griglia.
![[Pasted image 20240224041830.png]]
Assumendo che il campo $f(x,y)$ vari linearmente sul arco che collega due punti vicini abbiamo che vogliamo trovare una [[Superfici implicite|isosuperfice]] con un dato $\alpha$ .

Per fare cio si marcano i nodi in
- rosso se $f(x,y)<\alpha$
- blue se $f(x,y)>\alpha$
![[Pasted image 20240224034100.png]]
da qui si puo generare un algoritmo chiamato __marching square__. che segue come 
1. per ogni cella della griglia trova l intersezione con la isosurface
2. definisce un insieme per ogni permutazione di nodi blu e rossi 
per calcolare l intersezione si puo usare l [[Interpolazione Lineare|interpolazione lineare]] tra un nodo rosso $R$ e un nodo blu $B$, Possiamo dire che $$\begin{array}{}
\exists t & : & f(R)(1-t)+f(B)t = \alpha \\
	& \implies & t=\cfrac{\alpha-f(R)}{f(B)-f(R)}
\end{array}
$$
e sostituendo nella formula del [[Interpolazione Lineare|interpolazione lineare]] otteniamo l intersezione$$\boldsymbol{p}(R)(1-t)+\boldsymbol{p}(R)t=\boldsymbol{p}$$
![[Pasted image 20240224034049.png]]
utilizzando il set di $2^4=16$ [[Combinatoria|permutazioni]] e salvandoli una volta in una __loock-up table__  
![[Pasted image 20240224034011.png]]
si ottiene la superfice.
![[Pasted image 20240224034027.png]]



Passando ad una griglia 3D si avranno $8$ nodi e quindi andrebbero definiti $2^8=256$ poligoni uno per ogni permutazione. 
Pero queste possono essere ridotte ad un set piu piccolo di solo 15 ottenendo le mancanti per Rotazione o mirroring 
![[Pasted image 20240224034115.png]]



![[Pasted image 20240224043402.png]]
![[Pasted image 20240224043352.png]]