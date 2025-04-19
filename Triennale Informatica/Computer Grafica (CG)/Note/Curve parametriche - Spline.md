---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Curve parametriche - Spline
---
le __spline__ sono un classe di __[[Curve parametriche|curve parametriche]] [[Curve parametriche - Picewise|picewise]] [[Polinomi|polinomiche]]__ di grado $>1$
Sono basate sulla definizione di punti nello spazio detti __control point__ e la curva è generata a partire da questi punti. 

per rendere la curva piu smooth si usano delle funzioni di __blending__, dalla scelta della funzione dipendono le proprietà di [[Continuità di una funzione|continuità]], [[Funzioni differenziabili|differenziabilita]] e se la curva é  un [[Interpolazione VS approssimazione|interpolazione o una approssimazione]]  
La formulazione generale é la seguente
_sia_
- $P$ il __control polygon__ ovvero l [[Insiemi Matematici|insieme]] dei __control point__ di [[Cardinalità di un insieme|cardinalitá]]  $n$ 
- $p_i$ un __control point__
- $B_i(\cdot)$ la __funzione di blending__
_allora_ vale che $$C(t)=\sum^n_{i=0}p_iB_i(t) \ \ \ 0 \leq t \leq 1$$
