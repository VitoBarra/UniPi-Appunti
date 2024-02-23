---
tags:
  - ALG
Subject: "[[Algebra (ALG)]]"
Area: 
topic: 
SubTopic:
---
# Polinomio di Bernstein
---
il __[[Polinomi|polinomio]] di Bernstein__ é definito come$$B_{i,n}(x)=\begin{pmatrix} n \\ i \end{pmatrix}x^i(1-x)^{n-i}$$ che é uguale alla [[Variabili Aleatorie Notevoli - Binomiale|binomiale]]  $$\sum^n_{i=0} B_{i,n}(x)=1
$$ in piu altre proprietà importanti sono:
- $B_{i,n}(x)=0$ con $i \not \in [0,n]$ 
- $B_{i,n}(x)\geq 0$ con $x \in [0,1]$ 

l [[Insiemi Matematici|insieme]] di __polinomi di bernstein__ di grado $n$ tale che $\{ B_{0,n},B_{1,n},\dots B_{n,n} \}$ formano una [[Base di uno spazio vettoriale|base]] dello [[Spazio Vettoriale|spazio vettoriale]] dei [[Polinomi|polinomi]] chiamata __base di Bernstein__.

Un algoritmo [[Tipi di Errore nel calcolo numerico#Errore Algoritmo|stabile numericamente]] per calcolare i valori di questo polinomio è l [[Algoritmo di de Casteljau|algoritmo di de Casteljau]]

vale che si puo calcolare  $B_{i,n}(x)$ utilizzando la  [[Ricorsione|Relazione ricorsiva]] $$B_{i,n}(x)=
\begin{cases}
0  & if & i \not \in  [0,n]\\ 
B_{0,1}=1-x \\
B_{1,1}=x \\
xB_{i-1,n-1}(x)+(1-x)B_{i,n-1}(x)
\end{cases}
$$

questo tipo di polinomio viene utilizzato nel [[Interpolazione polinomiale|Interpolazione polinomiale]] e nelle [[Curve parametriche - Curve di Bezier|curve di bezier]]
![[Pasted image 20240221210726.png]]

##### Derivata del polinomi di bernstein
la [[Derivate|derivata]] di questo tipo di [[Polinomi|polinomi]] é calcolabile come 
$$\cfrac{d}{dx}B_{i,n}=n(B_{i-1,n-1}(x)-B_{i,n-1})$$