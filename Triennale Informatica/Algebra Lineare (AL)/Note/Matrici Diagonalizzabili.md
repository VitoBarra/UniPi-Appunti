---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---
# Matrici Diagonalizzabili
---
_sia_ un [[Isomorfismo e Endomorfismo#Endomorfismo|endomorfismo]] $F:V \rightarrow V$ e _diagonalizzabile_ $\iff$ esiste una base $\mathcal{B}$ di $V$ composta solo da [[Autovettori e Autovalori|autovettori]] $\iff$ la [[Matrice Associata]] $[f]^\mathcal{B}_\mathcal{B}$ e diagonale e contiene solo autovalori sulla diagonale

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
una matrice $A$ e diagonalizzabile se esiste una [[Matrice inversa|matrice invertibile]] $M$ tale che
$$
D = M^{-1}AM
$$
e $D$ e _diagonale_

> [!tip] osservazioni
> - Un [[Isomorfismo e Endomorfismo|endomorfismo]] $T : V \rightarrow V$ e diagonalizzabile $\iff$ la matrice associata $A = [T]^\mathcal{B}_\mathcal{B}$ e diagonalizzabile
> - solitamente le matrici diagonalizzabili sono le [[Matrici quadrate|matrice simmetriche]]

#### Teorema Criterio di diagonalizzabilità
Un [[Isomorfismo e Endomorfismo|endomorfismo]] $T : V \rightarrow V$ e _diagonalizzabile_ $\iff$ valgono entrambi i fatti seguenti:
- $p_T (\lambda)$ ha $n$ radici in $\mathbb{K}$, contate con [[Molteplicità algebrica e geometrica|molteplicità]]. quindi vi sono $\lambda_1,\dots, \lambda_n$ autovalori distinti associati a $n$ _autovettori_. puo succedere che $\lambda_{i}=\lambda_{j}$ nel valore
- $m_a(\lambda) = m_g(\lambda)$ per ogni autovalore $\lambda$ di $T$

### Esempio:

Mostriamo alcuni esempi in cui applichiamo il teorema di diagonalizzabilita.

**Esempio 5.2.13.** Studiamo la diagonalizzabilita su $\mathbb{R}$ della matrice

$$
A =
\begin{pmatrix}
3 & 0 & 0 \\
-4 & -1 & -8 \\
0 & 0 & 3
\end{pmatrix}.
$$

Si vede facilmente che il polinomio caratteristico e

$$
p_A(\lambda) = (3-\lambda)(-1-\lambda)(3-\lambda),
$$

quindi ha radici $\lambda_1 = 3$ con $m_a(\lambda_1) = 2$ e $\lambda_2 = -1$ con $m_a(\lambda_2) = 1$.

Tutte le radici di $p_A(\lambda)$ sono reali, quindi $A$ e diagonalizzabile se e solo se le molteplicita algebriche e geometriche di ciascun autovalore coincidono. Per il secondo autovalore $\lambda_2$ e facile: si ha $m_g(\lambda_2) = m_a(\lambda_2) = 1$.

Dobbiamo concentrarci solo sull'autovalore $\lambda_1$, che ha $m_a(\lambda_1) = 2$. Calcoliamo:

$$
m_g(3) = \dim V_3 = \dim \ker(A-3I) = 3 - \operatorname{rk}(A-3I).
$$

Nell'ultima uguaglianza abbiamo usato il teorema della dimensione. Quindi

$$
m_g(3) = 3 - \operatorname{rk}
\begin{pmatrix}
3-3 & 0 & 0 \\
-4 & -1-3 & -8 \\
0 & 0 & 3-3
\end{pmatrix}
= 3 - \operatorname{rk}
\begin{pmatrix}
0 & 0 & 0 \\
-4 & -4 & -8 \\
0 & 0 & 0
\end{pmatrix}
= 3 - 1 = 2.
$$

Abbiamo scoperto che $m_a(\lambda_1) = m_g(\lambda_1) = 2$ e quindi $A$ e diagonalizzabile.

**Esempio 5.2.14.** Studiamo la diagonalizzabilita su $\mathbb{R}$ della matrice

$$
A =
\begin{pmatrix}
3 & t+4 & 1 \\
-1 & -3 & -1 \\
0 & 0 & 2
\end{pmatrix},
$$

al variare del parametro $t \in \mathbb{R}$. Si vede facilmente che il polinomio caratteristico e

$$
p_A(\lambda) = (2-\lambda)(\lambda^2 + t - 5).
$$

Se $t > 5$, il membro di destra non ha radici reali, quindi $p_A(\lambda)$ ha una radice sola e $A$ non e diagonalizzabile. Se $t \leq 5$, il polinomio ha tre radici reali

$$
\lambda_1 = 2,
\qquad
\lambda_2 = \sqrt{5-t},
\qquad
\lambda_3 = -\sqrt{5-t}.
$$

Se le tre radici sono distinte, la matrice $A$ e diagonalizzabile. Restano da considerare i casi in cui le tre radici non sono distinte, e cioe i casi $t = 1$ e $t = 5$.

Se $t = 1$ gli autovalori sono $\lambda_1 = 2$, $\lambda_2 = 2$ e $\lambda_3 = -2$ e la matrice $A$ e

$$
A =
\begin{pmatrix}
3 & 5 & 1 \\
-1 & -3 & -1 \\
0 & 0 & 2
\end{pmatrix}.
$$

Calcoliamo la molteplicita geometrica dell'autovalore $2$:

$$
m_g(2) = 3 - \operatorname{rk}
\begin{pmatrix}
1 & 5 & 1 \\
-1 & -5 & -1 \\
0 & 0 & 0
\end{pmatrix}
= 3 - 1 = 2.
$$

Otteniamo $m_g(2) = 2 = m_a(2)$ e quindi $A$ e diagonalizzabile.

Se $t = 5$ gli autovalori sono $\lambda_1 = 2$, $\lambda_2 = 0$ e $\lambda_3 = 0$ e la matrice $A$ e

$$
A =
\begin{pmatrix}
3 & 9 & 1 \\
-1 & -3 & -1 \\
0 & 0 & 2
\end{pmatrix}.
$$

La molteplicita geometrica dell'autovalore $0$ e

$$
m_g(0) = 3 - \operatorname{rk}(A) = 3 - 2 = 1 \neq 2 = m_a(0).
$$

Quindi $A$ non e diagonalizzabile.

Riassumendo, la matrice $A$ e diagonalizzabile se e solo se $t < 5$.
