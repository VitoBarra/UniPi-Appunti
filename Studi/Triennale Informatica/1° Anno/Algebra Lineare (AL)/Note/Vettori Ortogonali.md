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

![[Studi/Triennale Informatica/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 19.png]]
Il [[Prodotto scalare euclideo (Dot product)|prodotto scalare euclideo]] anche detto __Dot product__ sul piano cartesiano $\mathbb{R}^2$ e se $\mathbb{R}^3$ corrisponde alle [[Rette perpendicolari|rette perpendicolari (o ortogonali)]] della geometria euclidea ma se si sceglie un  prodotto scalare diverso su $\mathbb{R}^2$ o $\mathbb{R}^3$ la nozione di __ortogonalità__ può cambiare considerevolmente.

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
