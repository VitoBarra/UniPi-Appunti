---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Ortogonalità E Ortonormalità
---

### Definizione
introduciamo alcune definizioni generali. sia $V$ munito di un prodotto scalare. due vettori $v,w \in V$ sono ortogonali se

$$
\langle v,w \rangle = 0
$$

Consideriamo il prodotto scalare euclideo su $\R^2$. i vettori ortogonali ad un vettore $\begin{pmatrix}a\\b \end{pmatrix}\not= 0$ sono quei vettori $\begin{pmatrix}x\\y \end{pmatrix}$ tali che

$$
ax + by =0
$$

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 19.png]]

Risolvendo il sistema, ne deduciamo che i vettori ortogonali ad $\begin{pmatrix}a\\b\end{pmatrix}$
 sono precisamente i vettori che stanno nella retta

$$
Span
\begin{pmatrix}
-b\\a
\end{pmatrix}
$$

il vettore $\begin{pmatrix}-b\\a\end{pmatrix}$ forma effettivamente un angolo retto con $\begin{pmatrix}a\\b\end{pmatrix}$ come mostrato chiaramente dalla  Figura 7.1. Il prodotto scalare euclideo sul piano cartesiano $\R^2$ e se $\R^3$ corrisponde alla familiare geometria euclidea; se però scegliamo un altro prodotto scalare su $\R^2$ o $\R^3$ la nozione di ortogonalità può cambiare considerevolmente.

### nota:

- due vettori colonna con $i \not=j$ della stessa base canonica sono ortogonali tra di loro infatti $\langle e_1,e_j \rangle = {}^te_i \cdot e^i =0$
- un prodotto scalare degenere può essere espresso anche con l’esistenza di un vettore $v \in V$ortogonale a tutto i vettore di $V$



## Vettori isotropi

i vettori isotropi sono vettori ortogonali a se stessi ovvero

$$
\langle v,v \rangle = 0
$$

sono inclusi nella definizione i vettori nulli

### Esistenza:

se il prodotto scalare è degenere esiste almeno uno vettore isotropo siccome esiste un $v \in V$ tale che $\langle v,w \rangle = 0\ \forall w \in V$  e quindi anche con se stesso



