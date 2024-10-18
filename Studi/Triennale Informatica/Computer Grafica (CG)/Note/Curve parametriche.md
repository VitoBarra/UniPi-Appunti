---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic:
---

# Curve parametriche
---
Una __curva parametrica__ é un modo per [[Rappresentazione di modelli 3D|rappresentare una curva in 3D]] ed è definita come 
_Sia_
- $A \subseteq  \mathbb{R}$ un [[Insiemi Matematici|insieme]]  chiamato lo __spazio dei parametri__
- $B \subseteq \mathbb{R}^3$ le coordinate dello spazio 3D
 _allora_ una __curva parametrica__ è definita da una [[Funzioni|funzione]]  $C:A \to B$ tale che $$C(t)=(X(t),Y(t),Z(t))$$ 
 Solitamene $A=[0,1]$ in questo modo $C(0)$ rappresenta l inizio della curva e $C(1)$ rappresenta la fine.
![[Pasted image 20240221031131.png]]
volendo disegnare una curva arbitraria risulta generalmente difficile trovare le formule $X(t),Y(t),Z(t)$ 

#### curve parametriche Picewise
le __curve parametriche picewise__ sono definite da una concatenazione di segmenti definita da una sequenza di equazioni che [[Interpolazione Lineare|interpolano linearmente]] tra un punto al altro, il modo di interpolare é completamente arbitrario e dipende dai range e dalle equazioni, si possono quindi creare segmenti dove l interpolazione é piu veloce o piu lenta.$$f(t)=\begin{cases}
eq_{1} & t\in  [a_0,a_1]\\ 
eq_{2} & t\in  [a_1,a_2] \\ 
 & \vdots \\ 
eq_{n} & t\in  [a_{n-1},a_n]
\end{cases}$$ 
![[Pasted image 20240222173959.png]]
#### Spline
le __spline__ sono un classe di __curve parametriche picewise [[Polinomi|polinomiche]]__ di grado $>1$
Sono basate sulla definizione di punti nello spazio detti __control point__ e la curva è generata a partire da questi punti. 

per rendere la curva piu smooth si usano delle funzioni di __blending__, dalla scelta della funzione dipendono le proprietà di [[Continuità di una funzione|continuità]], [[Funzioni differenziabili|differenziabilita]] e se la curva é  un [[Interpolazione VS approssimazione|interpolazione o una approssimazione]]  
La formulazione generale é la seguente
_sia_
- $P$ il __control polygon__ ovvero l [[Insiemi Matematici|insieme]] dei __control point__ di [[Cardinalità di un insieme|cardinalitá]]  $n$ 
- $p_i$ un __control point__
- $B_i(\cdot)$ la __funzione di blending__
_allora_ vale che $$C(t)=\sum^n_{i=0}p_iB_i(t) \ \ \ 0 \leq t \leq 1$$
