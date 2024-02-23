---
Subject: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---
# Vettori Ortogonali
---
_sia_ sia $V$ uno [[Spazio Vettoriale|spazio vettoriale]] munito di un [[Prodotto Scalare|prodotto scalare]] $\langle \cdot\rangle$ 
_allora_ due vettori $v,w \in V$ sono _ortogonali_ se$$
\langle v,w \rangle = 0
$$
_geometricamente_ significa che questi due vettori sono su [[Rette perpendicolari|perpendicolari]] 

Consideriamo il [[Prodotto scalare euclideo (Dot product)|prodotto scalare euclideo]] su $\mathbb{R}^2$. i vettori _ortogonali_ ad un vettore $\begin{pmatrix}a\\b \end{pmatrix}\not= 0$ sono quei vettori $\begin{pmatrix}x\\y \end{pmatrix}$ tali che

$$
ax + by =0
$$

![[UniPi-Appunti/Studi/Triennale Informatica/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 19.png]]
Figura 7.1. Il prodotto scalare euclideo sul piano cartesiano $\R^2$ e se $\R^3$ corrisponde alla familiare geometria euclidea; se però scegliamo un altro prodotto scalare su $\R^2$ o $\R^3$ la nozione di ortogonalità può cambiare considerevolmente.

Risolvendo il sistema, ne deduciamo che i vettori ortogonali ad $\begin{pmatrix}a\\b\end{pmatrix}$
 sono precisamente i vettori che stanno nella retta

$$
Span
\begin{pmatrix}
-b\\a
\end{pmatrix}
$$

il vettore $\begin{pmatrix}-b\\a\end{pmatrix}$ forma effettivamente un angolo retto con $\begin{pmatrix}a\\b\end{pmatrix}$ come mostrato chiaramente dalla  

### nota:
- due vettori colonna con $i \not=j$ della stessa base canonica sono ortogonali tra di loro infatti $\langle e_1,e_j \rangle = {}^te_i \cdot e^i =0$
- un prodotto scalare degenere può essere espresso anche con l’esistenza di un vettore $v \in V$ortogonale a tutti i vettore di $V$
