---
Subject: "[[Algebra Lineare (AL)]]"
tags:
  - AL
  - Imm2Text
topic:
---
# Matrici Diagonalizzabili
---
_sia_ un [[Isomorfismo e Endomorfismo#Endomorfismo|endomorfismo]] $F:V \rightarrow  V$ è _diagonalizzabile_ $\iff$ esiste una base $\mathcal{B}$ di $V$ è composta solo da [[Autovettori e Autovalori|autovettori]] $\iff$la [[Matrice Associata]] $[f]^\mathcal{B}_\mathcal{B}$ è diagonale e contiene solo autovalori sulla diagonale

$$
A=
\begin{pmatrix}
\lambda_1 &0 &\cdots &0 \\
0 &\lambda_2 &\cdots &0 \\
\vdots&\vdots &\ddots &\vdots \\
0 &0 &\cdots & \lambda_n
\end{pmatrix}
$$

### Matrici Diagonalizzabili
una matrice $A$ è diagonalizzabile se esiste una [[Matrice inversa|matrice invertibile]] $M$ tale che
$$
D = M^{-1}AM
$$
e $D$  è _diagonale_

> [!tip] osservazioni
> - Un [[Isomorfismo e Endomorfismo|endomorfismo]] $T : V \rightarrow V$ è diagonalizzabile $\iff$ la matrice associata $A = [T]^\mathcal{B}_\mathcal{B}$ è diagonalizzabile
> - solitamente le matrici diagonalizzabili sono le [[Matrici quadrate|matrice simmetriche]]

#### Teorema Criterio di diagonalizzabilità
Un [[Isomorfismo e Endomorfismo|endomorfismo]] $T : V \rightarrow V$ è _diagonalizzabile_ $\iff$ valgono entrambi i fatti seguenti:
- $p_T (\lambda)$ ha $n$ radici in $\mathbb{K}$, contate con [[Molteplicità algebrica e geometrica|molteplicità]]. quindi vi sono $\lambda_1,\dots, \lambda_n$ autovalori distinti associati a $n$ _autovettori_. puo succedere che $\lambda_{i}=\lambda_{j}$ nel valore
- $m_a(\lambda) = m_g(\lambda)$ per ogni autovalore $\lambda$ di $T$

### Esempio:
![[UniPi-Appunti/Studi/Triennale Informatica/1° Anno/Algebra Lineare (AL)/Media/Untitled 8.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 5.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/1° Anno/Algebra Lineare (AL)/Media/Untitled 2 4.png]]
