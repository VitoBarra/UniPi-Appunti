---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Autovettori e Autovalori
---

### Definizione:
sua di uno spazio vettoriale $V$su $\mathbb{K}$ e $T:V \rightarrow V$ un [[endomorfismo]] , chiamiamo autovalore un vettore $v \in V,v \not= 0$   e autovalore di $T$ associato a $v$  un qualunque $\lambda \in \mathbb{K}$ tale che

$$
T(v)=\lambda v
$$

### Osservazioni:

- tutti i vettori della retta $Span(v)$ sono autovettore con lo stesso autovalore
- Gli autovettori $v$ con autovalore $\lambda =0$ sono i vettori $v \not =0 \land v \in ker(T)$
- Gli autovettori $v$ con autovalore $\lambda =1$ sono i vettori $v \not =0$  che sono [[Punti Fissi]]


![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 7.png]]

![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 4.png]]

### Esistenza di autovettori:

- se $dim(\R^n)$ é dispari esiste sempre almeno un autovettore in $\R$ questo perché se $P_A(\lambda)$  ha grado dispari ha sempre una radice in $\R$
- Esiste sempre un autovalore nel campo $\mathbb{C}$ questo perché il [[polinomio caratteristico]] $P_A(\lambda)$ ha sempre una radice in $\mathbb{C}$

# Calcolare autovalori e autovettori

per calcolare i autovettori dobbiamo prima calcolare il polinomio caratteristico definito come

$$
P_A(\lambda)=det(A-\lambda I_n)=det
\begin{pmatrix}
a_{11}-\lambda &a_{12} &\cdots &a_{1n} \\

a_{21} &a_{22}-\lambda &\cdots &a_{2n} \\

\vdots &\vdots &\ddots &\vdots \\

a_{n1} &a_{n2} &\cdots &a_{nn}-\lambda \\
\end{pmatrix}
$$

il polinomio ha forma

$$
P_A(\lambda)=a_n\lambda^n+a_{n-1}\lambda^{n-1}+\dots+a_0
$$

è alcuni sui coefficienti sono noti

- $a_n = (-1)^n$
- $a_{n−1} = (−1)^{n−1}tr(A)$
- $a_0 =det(A)$

una volta trovato il polinomio caratteristico per trovare gli autovalori basta cercare le radici del polinomio

per trovare l'autovettore associato basta risolvere l’equazione

$$
Av=\lambda_iv
$$

oppure

$$
(A-\lambda I)v=0
$$
