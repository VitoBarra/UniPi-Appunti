---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
Area: 
topic: 
SubTopic: "[[Determinante di una matrice]]"
---
# Calcolare il determinante - Sviluppi di Laplace
---
Gli __sviluppi di Laplace__ sono una tecnica per calcolare il [[Determinante di una matrice|determinante]] di una matrice quadrata, soprattutto quando una riga o una colonna contiene molti zeri.

Sia $A$ una [[Matrici|matrice]] $n \times n$ con $n \geq 2$.

Per ogni posizione $(i,j)$ si considera il __minore__ $M_{ij}$, cioe' il determinante della sottomatrice ottenuta eliminando da $A$ la $i$-esima riga e la $j$-esima colonna.

Il corrispondente __cofattore__ e'
$$
C_{ij} = (-1)^{i+j} M_{ij}
$$

Lo sviluppo di Laplace lungo la riga $i$ e' allora
$$
\det(A) = \sum_{j=1}^{n} a_{ij} C_{ij} = \sum_{j=1}^{n} (-1)^{i+j} a_{ij} M_{ij}
$$

In modo del tutto analogo, sviluppando lungo la colonna $j$, si ha
$$
\det(A) = \sum_{i=1}^{n} a_{ij} C_{ij} = \sum_{i=1}^{n} (-1)^{i+j} a_{ij} M_{ij}
$$

## Schema dei segni
I segni dei cofattori seguono sempre il disegno a scacchiera
$$
\begin{pmatrix}
+ & - & + & - & \cdots \\
- & + & - & + & \cdots \\
+ & - & + & - & \cdots \\
- & + & - & + & \cdots \\
\vdots & \vdots & \vdots & \vdots & \ddots
\end{pmatrix}
$$
cioe' ogni cofattore ha segno dato da $(-1)^{i+j}$.

## Idea intuitiva
L'idea e' che il determinante di una matrice grande venga riscritto come somma di determinanti di matrici piu piccole.

Conviene scegliere una riga o una colonna con molti zeri, perche' i termini con $a_{ij} = 0$ si annullano e il calcolo si semplifica molto.

In pratica:
- scegli una riga o una colonna;
- per ogni elemento non nullo associ il segno corretto;
- elimini la sua riga e la sua colonna;
- calcoli il determinante della sottomatrice restante;
- sommi tutti i contributi.
