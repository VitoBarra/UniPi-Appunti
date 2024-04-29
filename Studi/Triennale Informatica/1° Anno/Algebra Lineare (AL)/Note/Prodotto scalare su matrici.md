---
Subject: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Prodotto scalare su matrici
---
il _prodotto scalare su matrici_ è un tipo di [[Prodotto Scalare]] definito come segue.
#### Definizione
_sia_ [[Matrici|matrice]] $S$ una matrice [[Matrici quadrate|simmetrica]] 
_allora_ il prodotto scalare tra matrice è definito come$$
g_S(x,y) = {}^tx \cdot S \cdot y
$$
Osservazioni:
il fatto che sia una _matrice simmetrica_ è necessario per soddisfare l assioma $\langle v,w\rangle=\langle w,v\rangle$ del _prodotto scalare_

- se utilizziamo come input i vettori colonna delle basi canoniche possiamo “selezionare” un elemento della matrice infatti:

$$
g_S(e_i,e_j) = {}^te_i \cdot S \cdot e_j = S_{ij}
$$

Nota: questo funziona anche se la matrice NON è simmetrica ma non è più considerabile prodotto scalare

- Se la matrice $S$ su cui è definita il prodotto scalare $g_S$ è la matrice identità allora otteniamo il prodotto scalare euclideo infatti:

    $$
    g_{I_n}(x,y)= {}^tx \cdot I_n \cdot y = {}^tx\cdot y=x_1y_y + \dots + x_ny_y
    $$

- Se la matrice $S$ su cui è definita il prodotto scalare $g_S$ è una matrice diagonale $D$ allora otteniamo un prodotto scalare più semplice infatti:

$$
g_D(x,y)=d_1x_1y_1 +\cdots+d_n  x_ny_n
$$

in questo caso è anche facile classificare il prodotto scalare infatti

- $g_D(x,y)$ è definito positivo $\iff d_i>0\ \ \forall i$
- $g_D(x,y)$ è non degenere $\iff d_i \not = 0 \ \forall i$

