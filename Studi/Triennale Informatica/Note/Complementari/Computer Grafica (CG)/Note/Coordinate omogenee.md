---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
  - AL
---


# Coordinate omogenee
---
le _coordinate_ omogenee sono un sistema di coordinate per rappresentano _punti_  $\boldsymbol{p}$ e _vettori_ $\boldsymbol{v}$ come segue
$$\boldsymbol{p}=\begin{bmatrix}
p_{x}\\p_{y}\\p_{z} \\ 1 
\end{bmatrix}
\ \ \ \ \ \boldsymbol{v}=\begin{bmatrix}
v_{1}\\v_{2}\\v_{3} \\0
\end{bmatrix}$$ dove $p_i$ e $v_i$ i componenti delle coordinate nel [[Piano cartesiano|piano cartesiano]]

per distinguere tra vettori e punti si guarda al ultimo componente e infatti abbiamo che con 
- $1$   rappresenta un _punto_ $\boldsymbol{p}$ 
- $0$ rappresenta un _vettore_ $\boldsymbol{v}$


> [!tip]
> sono stati usati $3$ componenti del vettore ma le definizioni restano valide per $n$ componenti

##### Operazioni
questa sistema di coordinate si definiscono le [[Operazioni chiuse|operazioni chiuse]] tra _punti_ e _vettori_ 
- _adizione punto-vettore_ $1+0=1$ e quindi è un punto
- _adizione vettore-vettore_ $0+0=0$ e quindi è un vettore
- _sottrazione punto-vettore_ $1-1=0$ e quindi è un vettore
e quindi le operazioni restituiscono una coordinata omogenea

##### Equivalenza punti vettori
per semplificare l uso delle coordinate omogenee si definisce la seguente equivalenza 
Sia
- $p$ un punto 
- $\boldsymbol{\mathit{v}}$ il _vettore_ tra l origine $O$ e il _punto_ $\boldsymbol{p}$
$$\boldsymbol{\mathit{v}}=\boldsymbol{p}-\begin{bmatrix}
0\\0\\0\\1
\end{bmatrix}\ \ \ \ \boldsymbol{p}=\boldsymbol{\mathit{v}}+\begin{bmatrix}
0\\0\\0\\1
\end{bmatrix}$$

##### Forma canonica
Nelle coordinate omogenee __punti__ diversi possono rappresentare lo stesso punto in [[Piano cartesiano|coordinate cartesiane]]  infatti abbiamo che 
$$\underbrace{ \boldsymbol{p} }_{ cartesian }=\underbrace{\lambda
 \begin{bmatrix}
p_{x}\\p_{y}\\p_{z} \\ 1 
\end{bmatrix} }_{ Homogeneus }$$dove se $\lambda =1$ vengono dette in __forma canonica__ e nel caso dei punti per passare dalla forma non canonico ad una canonica basta dividere per l ultimo componente. 

Questo __non__ vale per i vettori che invece hanno una rappresentazione __unica__ 


