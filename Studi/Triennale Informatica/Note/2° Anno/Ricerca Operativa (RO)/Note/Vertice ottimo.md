---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Vertice ottimo
---

**# Teorema (condizione sufficiente di ottimalità)**

Sia $\overline{x}$ una soluzione di base primale ammissibile relativa alla [[Basi e vertici|base]] $B$. Se la soluzione di base duale $\overline{y}$  relativa alla stessa base $B$ e ammissibile allora $\overline{x}$ è ottima per il problema primale e $\overline{y}$ è ottima per il duale.

### Dimostrazione

Due soluzioni di base $\overline{x} \text{ e } \overline{y}$ relative alla stessa [[Basi e vertici|base]] sono sempre in scarti
complementari

$$
\overline{y}(b-A\overline{x}) =
(\overline{y}_B^T,\overline{y}_N^T)
\begin{pmatrix}
b_B-A_B\overline{x} \\
b_N-A_N\overline{x}
\end{pmatrix} =
(\overline{y}_B^T,0)
\begin{pmatrix}
0 \\
b_N-A_N\overline{x}
\end{pmatrix} =0
$$

Se $\overline {x}$  e $\overline{y}$ sono anche ammissibili rispettivamente per il primale e duale, allora sono anche ottime

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 20.png]]

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 15.png]]
