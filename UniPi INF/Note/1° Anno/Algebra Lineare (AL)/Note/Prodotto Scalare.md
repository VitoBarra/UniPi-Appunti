---
type: nota
course: Algebra Lineare
topic: 
tags: AL Imm2Text 
---

Prev: [[Algebra Lineare (AL)]]

# Prodotto Scalare
---

### Definizione
Il prodotto scalare è un operazione definita su due vettori è restituiscono un numero in un campo $\mathbb{K}$ che di solito è il campo $\mathbb{R}$

![[UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 22.png]]

### Classificazione  prodotti scalari:

![[UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 14.png]]

![[UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 2 11.png]]


## Esempi di Prodotto scalare:

Alcuni esempi del tipo

$$
\R^n \times \R^n \rightarrow\R
$$

sono

### Prodotto Scalare Euclideo:

si para di prodotto scalare euclideo se si prendono in considerazione due vettori ed è definito come

$$
\langle x,y\rangle = {}^tx \cdot y
$$

infatti:

Nell’espressione  ${}^tx \cdot y$ il vettore ${}^t x$ è un vettore riga e $\cdot$ indica il prodotto
fra matrici. In altre parole, se

$$
x=
\begin{pmatrix}
x_1 \\
\vdots \\
x_n
\end{pmatrix}

y =
\begin{pmatrix}
y_1 \\
\vdots \\
y_n
\end{pmatrix}
$$

allora

$$
\langle x,y \rangle = (x_1, \dots,x_n) \cdot
\begin{pmatrix}
y_1 \\
\vdots \\
y_n
\end{pmatrix} =
x_1y_1 +\cdots+x_ny_n
$$

### Prodotto scalare su matrice

si parla di prodotto scalare su matrice $S$ se questa é [[Tipi di matrice quadrata|simmetrica]] (cosa necessaria per soddisfare l assiama 5) ed è definita come

$$
g_S(x,y) = {}^tx \cdot S \cdot y
$$

Osservazioni:

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

