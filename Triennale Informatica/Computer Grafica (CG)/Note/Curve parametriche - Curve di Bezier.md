---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: "[[Curve parametriche]]"
---

# Curve parametriche - Curve di Bezier
---
le __curve di Bezier__ sono un tipo di [[Curve parametriche|curva parametrica]] di classe __[[Curve parametriche#Spline|Spline]]__ e sono definite come
_sia_
- $\boldsymbol{P}$ il __control polygon__ ovvero l [[Insiemi Matematici|insieme]] dei __control point__ di [[Insiemi - Cardinalita|cardinalita]]  $n$
- $P_i$ un __control point__
- $B_{i,k}(\cdot)$ la __funzione di blending__ realizzata con il [[Polinomio di Bernstein|polinomio di Bernstein]] di grado $k$
_allora_ le curve di Bezier sono definite come $$P(t)=\sum^n_{i=0}p_iB_{i,n-1}(t) \ \ \ 0 \leq t \leq 1$$
e valgono le seguenti proprietà:
1. la curva inizia al punto $p_0$ e finisce al punto $p_n$
2. la curva che parte da $p_0$ è [[Retta tangente|tangente]] al segmento $p_1-p_0$
3. la curva che finisce in $p_n$ è [[Retta tangente|tangente]] al segmento $p_n-p_{n-1}$
4. la curva [[Interpolazione VS approssimazione|approssima]] i punti.
5. Siccome la somme di tutti i termini del [[Polinomio di Bernstein|polinomio di bernstein]]  $\sum^n_{i=0}B_{i,n}(t)=1$ si ha che la curva di bezier é sempre al intero del [[Convessita#Involucro Convesso|involucro convesso]] dei __Control point__ 
	![[Pasted image 20240222022108.png]]

con $2$ __control point__ $p_0,p_1$ avremmo che il grado del [[Polinomio di Bernstein|polinomio di bernstain]] è $1$, le curve di questo tipo sono dette __curva di bezier lineare__. Il punto $p_1$ viene unito con il punto $p_2$ con una linea ed espandendo la sommatoria abbiamo che la curva viene calcolata come$$P(t)=p_0(1-t)+p_1t$$ e questa corrisponde al [[Interpolazione Lineare|interpolazioni lineare]]



con $4$ __control point__ $p_0,p_1,p_2,p_3$ avremmo che il grado del [[Polinomio di Bernstein|polinomio di bernstain]] è $3$ le curve di questo tipo sono dette __curve di bezier cubiche__. Espandendo la sommatoria abbiamo che la curva viene calcolata come$$P(t)=(1-t)^3p_0+3t(1-t)^2p_1+3t^2(1-t)p_2+t^3p_3$$ che riscrivendo sotto forma di matrice si ha che $$
\begin{array}{}
P(t) & = & \begin{bmatrix}
(1-t)^3 & t(1-t)^2  & t^2(1-t) & t^3
\end{bmatrix} 
\begin{bmatrix}
p_0\\p_1\\p_2\\p_3
\end{bmatrix} & = \\
& = & \begin{bmatrix} 1 & t & t^2 & t^3\end{bmatrix} 
 \begin{bmatrix}
1 & 0 & 0 & 0 \\
-3 & 3 & 0 & 0 \\
3 & -6 & 3 & 0 \\
-1 & 3 & -3 & 1
\end{bmatrix}
\begin{bmatrix}
p_0\\p_1\\p_2\\p_3
\end{bmatrix}
\end{array}
$$
e [[Prodotto tra matrici|moltiplicando le matrici]] si puo verificare che si torna alla forma originale
![[Pasted image 20240221210633.png]]
le __curve di bezier__ si possono anche realizzare con gradi superiori 
![[Pasted image 20240222020908.png]]

##### Tangente alla curva di bezier
si puo calcolare la retta tangente alla curva di bezier utilizzando le [[Derivate|derivate]].
per derivare la curva parametrica avremmo che dobbiamo calcolare $$f'(t)=\sum^n_{i=0}\cfrac{d}{dt}B_{i,n}(t)$$ e abbiamo la derivata del [[Polinomio di Bernstein|polinomio di Bernstein]] ha una formula nota che segue come  $$\cfrac{d}{dx}B_{i,n}=n(B_{i-1,n-1}(x)-B_{i,n-1})$$ e unendo le due cose si ottiene che $$f'(t)=n\sum^{n-1}_{i=0}\boldsymbol{p}_{i+1}B_{i-1,n-1}(t)-\boldsymbol{p}_iB_{i,n-1}(t)$$
e da questa si puo calcolare il __vettore di tangente unitario__ come $$T(f(t))=\cfrac{f'(t)}{\| f'(t) \| }$$

##### Cammino di bezier
con la definizione della __curva di bezier__ abbiamo che al aumentare dei punti di controllo aumenta il grado del [[Polinomio di Bernstein|polinomio di bernstein]] da usare, questo pero é poco efficiente e si tende ad utilizzare i __cammino di bezier__, che ci permettono di usare un [[Polinomio di Bernstein|polinomio di bernstein]] di grado basso e di costruire curve piu complesse  

per costruire un __cammino di bezier__ si sceglie un grado $n$ del [[Polinomio di Bernstein|polinomio di bernstein]] e di conseguenza anche il numero di __control point__, e per ottenere la curva desiderata si uniscono più __curve di Bezier__ fatte con il numero di __control point__ scelto.
l' unione delle curve individuali deve essere fatta in modo da garantire la [[Continuità di una funzione|continuità]] e la [[Smoothness di una superfice|smoothness]] della curva finale per fare ciò ci sono i seguenti criteri.
1) continuità : se l'__ultimo punto__ di una curva viene usato come __primo punto__ della successiva, questo garantisce la continuità grazie alle proprietà delle __curve di bezier__
	- ![[Pasted image 20240222182447.png]]
2) smooth: se vale $1$ e il penultimo e l ultimo punto della prima curva assieme al primo e al secondo della seconda curva devono essere [[Colinearita|collineari]] e quindi hanno la stessa __tangente unitaria__.
	- ![[Pasted image 20240222182458.png]]
	- (nel esempio $v_1,v_2=v_3,v_4$ collineari) 
1) perfettamente smooth: se vale $2$ e vale che la [[Norme Matriciali e Norme Vettoriali|norma]] tra ultimo meno penultimo è uguale alla norma di primo meno secondo, ovvero hanno la stessa [[Derivate|derivata]] seconda
	- ![[Pasted image 20240222182516.png]]
	- nel esempio $\| v_2-v_3 \| = \| v_0-v_1 \|$

![[Pasted image 20240222175645.png]]