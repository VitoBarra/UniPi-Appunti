---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---

# Teorema Spettrale
---

### Enunciato

_sia_ $T : V \rightarrow V$ un [[Isomorfismo e Endomorfismo|endomorfismo]] autoaggiunto su uno spazio euclideo reale.

_allora_ $T$ e diagonalizzabile rispetto a una [[Base di uno spazio vettoriale|base]] [[Vettori Ortonormali|ortonormale]] di [[Autovettori e Autovalori|autovettori]].

In particolare:

- tutti gli autovalori di $T$ sono reali;
- esiste una base ortonormale $\mathcal{B}$ di $V$ formata da autovettori di $T$;
- la [[Matrice Associata]] $[T]^\mathcal{B}_\mathcal{B}$ e diagonale.

Se gli autovettori della base sono $v_1, \dots, v_n$ e i rispettivi autovalori sono $\lambda_1, \dots, \lambda_n$, allora

$$
[T]^\mathcal{B}_\mathcal{B} =
\begin{pmatrix}
\lambda_1 & 0 & \cdots & 0 \\
0 & \lambda_2 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & \lambda_n
\end{pmatrix}.
$$

### Versione matriciale

Se $A$ e una matrice reale simmetrica, allora il teorema spettrale dice che $A$ e ortogonalmente diagonalizzabile, cioe esiste una matrice ortogonale $Q$ tale che

$$
Q^T A Q = D,
$$

dove $D$ e diagonale.

Equivalentemente,

$$
A = Q D Q^T.
$$

Le colonne di $Q$ sono una base ortonormale di autovettori di $A$, mentre gli elementi diagonali di $D$ sono gli autovalori di $A$.

>[!tip]
> tutte le matrici simmetriche hanno autovalori reali
> e ammettono una base ortonormale di autovettori.

### Conseguenze utili

- una matrice simmetrica e sempre [[Matrici Diagonalizzabili|diagonalizzabile]];
- la diagonalizzazione puo essere fatta con un cambio di base ortonormale;
- autovettori associati ad autovalori distinti sono ortogonali;
- lo studio di forme quadratiche e [[Matrici Definite|matrici definite]] si riconduce a una matrice diagonale.

### Collegamento con le forme quadratiche

Se $A$ e simmetrica e

$$
q(x) = x^T A x,
$$

allora scegliendo una base ortonormale di autovettori la forma quadratica diventa

$$
q(x) = \lambda_1 x_1^2 + \cdots + \lambda_n x_n^2,
$$

cioe una somma di quadrati pesati dagli autovalori.
