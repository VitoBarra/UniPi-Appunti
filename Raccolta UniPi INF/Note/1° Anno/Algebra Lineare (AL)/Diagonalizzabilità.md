---
type: nota
course: Algebra Lineare
topic: 
tags: AL Imm2Text 
---

Prev: [[Algebra Lineare (AL)]]

# Diagonalizzabilità
---

# Endomorfismi Diagonalizzabili

sia un endomorfismo $F:V \rightarrow  V$è diagonalizzabile $\iff$ esiste una base $\mathcal{B}$ di $V$ è composta solo da autovettori $\iff$la matrice associata $[f]^\mathcal{B}_\mathcal{B}$ è diagonale e contiene solo autovalori sulla diagonale

$$
A=
\begin{pmatrix}
\lambda_1 &0 &\cdots &0 \\
0 &\lambda_2 &\cdots &0 \\
\vdots&\vdots &\ddots &\vdots \\
0 &0 &\cdots & \lambda_n
\end{pmatrix}
$$

# Matrici Diagonalizzabili

una matrice $A$ è diagonalizzabile se esiste una matrice invertibile $M$ tale che

$$
D = M^{-1}AM
$$

e $D$  è diagonale

# Osservazioni:

Un endomorfismo $T : V \rightarrow V$ è diagonalizzabile $\iff$ la matrice associata $A = [T]^\mathcal{B}_\mathcal{B}$ è diagonalizzabile

## (Criterio)Teorema di diagonalizzabilità:

Un endomorfismo $T : V \rightarrow V$ è diagonalizzabile se e solo se valgono entambi i fatti seguenti:

- $p_T (\lambda)$ ha $n$ radici in $\mathbb{K}$, contate con molteplicità. quindi vi sono $\lambda_1,\dots, \lambda_k$ distinti
- $m_a(\lambda) = m_g(\lambda)$ per ogni autovalore $\lambda$ di $T$

### esempio:

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 8.png]]

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 1 5.png]]

[[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/-AL Media/Untitled 2 4.png]]
