---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Coordinate Rispetto ad una base
---

### Algoritmo
per trovare le coordinate rispetto ad una [[Base di uno spazio vettoriale]] si utilizza un vettore generico di codiante e utilizziamo i parametri come coefficienti per la base scelta risolvendo il [[Soluzioni di un sistema lineare|sistema Lineare]] troveremo la relazione che lega le coordinate alla base

### Esempi

trovare le codiante di un generico vettore $\begin{pmatrix} x \\ y\end{pmatrix}$ con la base $\begin{pmatrix} 1 \\0\end{pmatrix}\begin{pmatrix}0 \\1\end{pmatrix}$:

$$
\begin{pmatrix}
x\\y
\end{pmatrix}
=
t
\begin{pmatrix}
1\\0
\end{pmatrix}
+
u
\begin{pmatrix}
0\\1
\end{pmatrix}

$$

$$
\begin{cases}
x=t \\
y = u
\end{cases}

$$

$$
t = x\ \ \ \ \ \ \ \ u = y
$$

---

  trovare le codiante di un generico vettore $\begin{pmatrix}x \\ y \end{pmatrix}$con la base $\begin{pmatrix}-1\\1\end{pmatrix}\begin{pmatrix}2 \\1\end{pmatrix}$:

$$
\begin{pmatrix}
x\\y
\end{pmatrix}
=
t
\begin{pmatrix}
-1\\1
\end{pmatrix}
+
u
\begin{pmatrix}
2\\1
\end{pmatrix}

$$

$$
\begin{cases}
x=-t+2u \\
y = t + u
\end{cases}

$$

$$
t= \frac{-x+2y}{3}\ \ \ \ \ \ \ \ u= \frac{x+y}{3}
$$
