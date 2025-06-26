---
Course: "[[Ricerca Operativa (RO)]]"
Course 2: "[[3D Geometry for Modeling and Processing (3GMP)]]"
topic: nota
tags:
  - RO
---

# Poliedro
---
Un **poliedro** in $\mathbb{R}^2$ e l’intersezione di un numero finito di [[Semispazio|semispazi chiusi]], oppure, è l’insieme delle soluzioni di un sistema di disequazioni lineari $Ax \leq b$.


un **poliedro** $P$  è detto **limitato** se esiste $M > 0$ tale che $||x|| \leq M \ \ \forall x \in P$ ossia se è contenuto in una opportuna sfera concertata nel origine



### Vertici (Geometrici)

un vertice di un poliedro è un punto $x$  del poliedro che non si può esprimere come [[Convessita#Combinazione convessa|combinazione convessa]] propria di altri punti del poliedro. L’insieme dei vertici di un poliedro $P$ vene denotato con $vert(P)$

# Vertici (Algebrici)

Sia un poliedro $P = \{x \in \mathbb{R}^n \ | \ Ax \leq b   \}$ ,  un suo vertice è una soluzione $\overline{x}$ di [[Basi e vertici|base]] primale

>[!abstract] ### Corollario
in un poliedro $P =\{x \in \mathbb{R} \ | \ Ax \leq b\}$, dove $A$ è una atrice $m \times n$
   $vert(P) \not= \emptyset\iff rank(A) =n \iff lineal(P) = \{0\}$

<aside>

</aside>

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 1 17.png]]

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 2 11.png]]

---

## Direzione di recessione

Una direzione di recessione per un poliedro $P$ è un vettore $d$ tale che

$$
x+\lambda d \in P \\
\forall x \in P, \forall\lambda \geq 0
$$

Quindi $d$ è una direzione di recessione se $P$ contiene tutte le semirette di direzione $d$ uscenti
da punti appartenenti a $P$. L’insieme delle direzioni di recessione di  viene denotato con
$rec (P)$.

Ovviamente $0 \in rec(P)$ e si osserva che se un poliedro $P$ è limitato allora $rec (P) = \{0\}$

### Teorema

Se un poliedro $P = \{x \in \mathbb{R}^n \ | \ Ax \leq b\}$, allora

$$
rec(P) = \{x\in\mathbb{R}\ |\ Ax \leq 0 \}
$$

---

### Linearità

Una direzione di linearità per un poliedro $P$ è un vettore $d$ tale che

$$
d \in rec(P)\ \ \ \ \ \ \ -d \in rec(P)
$$

ossi $d$ è una direzione di linearità se $P$ contiene tutte le rette di direzione $d$ passanti per punti appartenenti a $P$. l insieme delle direzione di linearità di $P$ viene denotata con $lineal(P)$

### Teorema

Se un poliedro P $= \{x \in \mathbb{R}^n \ | \ Ax \leq b\}$, allora

$$
lineal(P) = \{x\in\mathbb{R}\ |\ Ax = 0 \}
$$

$lineal(P)$ è un [[Sottospazio Vettoriale]].

![[Untitled 3 9.png]]