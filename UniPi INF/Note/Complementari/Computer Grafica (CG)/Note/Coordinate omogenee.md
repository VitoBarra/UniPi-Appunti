---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Coordinate omogenee
---
le _coordinate_ omogenee sono un sistema di coodinate per rappresentano _punti_ e _vettori_ come segue
$$\boldsymbol{p}=\begin{bmatrix}
p_{x}\\p_{y} \\ 1 
\end{bmatrix}
\ \ \ \ \ \boldsymbol{\mathit{v}}=\begin{bmatrix}
v_{1}\\v_{2} \\0
\end{bmatrix}$$
dove per distingue i due si guardo al ultimo valore
- $\boldsymbol{p}$ rappresenta un _punto_ con 1 come ultimo valore e  _rappresenta_ 
- $\boldsymbol{\mathit{v}}$ rappresenta un _vettore_ con 0 come ultimo valore

questa notazione preserva le operazioni definite tra _punti_ e _vettori_ infatti 
_adizone punto-vettore_ $1+0=1$ e quindi è un punto
_adizione vettore-vettore_ $0+0=0$ e quindi è un vettore
_sotrazione punto-vettore_ $1-1=0$ e quindi è un vettore

Come definito prima.
##### Equivalenza punti vettori
per semplificare l uso delle coordinate omogenee si definisce la seguente equivalenza $$\boldsymbol{\mathit{v}}=\boldsymbol{p}-\begin{bmatrix}
0\\0\\1
\end{bmatrix}\ \ \ \ \boldsymbol{p}=\boldsymbol{\mathit{v}}+\begin{bmatrix}
0\\0\\1
\end{bmatrix}$$
dove $\boldsymbol{\mathit{v}}$ indica il _vettore_ tra l origine e il _punto_ $\boldsymbol{p}$ e $\boldsymbol{p}$ rappresenta il punto raggiunto dal vettore $\mathit{\boldsymbol{v}}$. _Ricordando_ che l ultimo valore del vettore non è una coordinata ma indica solo se il vettore rappresenta un _punto_ o una _vettore_