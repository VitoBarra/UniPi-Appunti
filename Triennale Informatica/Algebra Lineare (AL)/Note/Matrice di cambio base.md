---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---


# Matrice di cambio base
---

### Definizione

sia $V$ uno spazio vettoriale e date due basi $\mathcal{B}$ e $\mathcal{C}$ di $V$ la matrice di cambio di base da $\mathcal{B}$ a $\mathcal{C}$ e la [[Matrice Associata]] con $f = id_V$

$$
A=[id_V]^\mathcal{B}_\mathcal{C}
$$

infatti vale che $\forall v\in V$

$$
[v]_\mathcal{C} = A[v]_\mathcal{B}
$$

dove $[v]_\mathcal{C}$ sono le coordinate di $v$ rispetto alla base $\mathcal{C}$.

Sia ora

$$
f : V \to W
$$

una applicazione lineare. Siano $\mathcal{B}_1, \mathcal{B}_2$ due basi di $V$ e $\mathcal{C}_1, \mathcal{C}_2$ due basi di $W$. Applicando la proposizione sul cambio di base troviamo:

$$
[f]^{\mathcal{B}_2}_{\mathcal{C}_2} = [id_W]^{\mathcal{C}_1}_{\mathcal{C}_2} \cdot [f]^{\mathcal{B}_1}_{\mathcal{C}_1} \cdot [id_V]^{\mathcal{B}_2}_{\mathcal{B}_1}.
$$

Per passare da $[f]^{\mathcal{B}_1}_{\mathcal{C}_1}$ a $[f]^{\mathcal{B}_2}_{\mathcal{C}_2}$ e sufficiente moltiplicare a sinistra e a destra per le matrici di cambiamento di base.

**Esempio 4.3.14.** Nell'[[Matrice Associata|Esempio 4.3.2]] abbiamo analizzato un'applicazione lineare

$$
f : \mathbb{R}_2[x] \to \mathbb{R}^2
$$

e calcolato la matrice associata rispetto alle basi canoniche

$$
\mathcal{C}' = \{1, x, x^2\}
\qquad \text{e} \qquad
\mathcal{C} = \{e_1, e_2\}.
$$

Il risultato era il seguente:

$$
[f]^{\mathcal{C}'}_{\mathcal{C}} =
\begin{pmatrix}
1 & 2 & 4 \\
1 & -2 & 4
\end{pmatrix}.
$$

Successivamente abbiamo cambiato $\mathcal{C}$ con

$$
\mathcal{B} = \left\{ \begin{pmatrix}1\\-1\end{pmatrix}, \begin{pmatrix}0\\1\end{pmatrix} \right\}.
$$

La matrice di cambiamento di base da $\mathcal{B}$ a $\mathcal{C}$ e molto semplice, perche le coordinate di un vettore rispetto a $\mathcal{C}$ sono il vettore stesso e quindi basta affiancare i vettori di $\mathcal{B}$; otteniamo

$$
[id]^{\mathcal{B}}_{\mathcal{C}} =
\begin{pmatrix}
1 & 0 \\
-1 & 1
\end{pmatrix}.
$$

Adesso calcoliamo l'inversa e troviamo

$$
[id]^{\mathcal{C}}_{\mathcal{B}} =
\begin{pmatrix}
1 & 0 \\
1 & 1
\end{pmatrix}.
$$

Quindi la matrice associata a $f$ nelle basi $\mathcal{C}'$ e $\mathcal{B}$ e

$$
[f]^{\mathcal{C}'}_{\mathcal{B}} = [id]^{\mathcal{C}}_{\mathcal{B}} [f]^{\mathcal{C}'}_{\mathcal{C}} =
\begin{pmatrix}
1 & 0 \\
1 & 1
\end{pmatrix}
\begin{pmatrix}
1 & 2 & 4 \\
1 & -2 & 4
\end{pmatrix}
=
\begin{pmatrix}
1 & 2 & 4 \\
2 & 0 & 8
\end{pmatrix}.
$$

**Esempio 4.3.15.** Nell'[[Matrice Associata|Esempio 4.3.3]] abbiamo considerato un'applicazione lineare

$$
f : \mathbb{C}^2 \to \mathbb{C}^3
$$

e calcolato la matrice associata rispetto alle basi canoniche $\mathcal{C}$ e $\mathcal{C}'$ di $\mathbb{C}^2$ e $\mathbb{C}^3$:

$$
[f]^{\mathcal{C}}_{\mathcal{C}'} =
\begin{pmatrix}
1 & -1 \\
2 & 0 \\
0 & 1
\end{pmatrix}.
$$

Successivamente abbiamo cambiato entrambe le basi con

$$
\mathcal{B} = \left\{ \begin{pmatrix}1\\1\end{pmatrix}, \begin{pmatrix}1\\-1\end{pmatrix} \right\},
\qquad
\mathcal{B}' = \left\{ \begin{pmatrix}1\\1\\0\end{pmatrix}, \begin{pmatrix}0\\1\\1\end{pmatrix}, \begin{pmatrix}1\\0\\1\end{pmatrix} \right\}.
$$

Calcoliamo le matrici di cambiamento di base:

$$
[id_{\mathbb{C}^2}]^{\mathcal{B}}_{\mathcal{C}} =
\begin{pmatrix}
1 & 1 \\
1 & -1
\end{pmatrix},
\qquad
[id_{\mathbb{C}^3}]^{\mathcal{B}'}_{\mathcal{C}'} =
\begin{pmatrix}
1 & 0 & 1 \\
1 & 1 & 0 \\
0 & 1 & 1
\end{pmatrix}.
$$

L'inversa della seconda e

$$
[id_{\mathbb{C}^3}]^{\mathcal{C}'}_{\mathcal{B}'} = \frac{1}{2}
\begin{pmatrix}
1 & 1 & -1 \\
-1 & 1 & 1 \\
1 & -1 & 1
\end{pmatrix}.
$$

Troviamo infine

$$
[f]^{\mathcal{B}}_{\mathcal{B}'} = [id_{\mathbb{C}^3}]^{\mathcal{C}'}_{\mathcal{B}'} \cdot [f]^{\mathcal{C}}_{\mathcal{C}'} \cdot [id_{\mathbb{C}^2}]^{\mathcal{B}}_{\mathcal{C}}
$$

$$
= \frac{1}{2}
\begin{pmatrix}
1 & 1 & -1 \\
-1 & 1 & 1 \\
1 & -1 & 1
\end{pmatrix}
\begin{pmatrix}
1 & -1 \\
2 & 0 \\
0 & 1
\end{pmatrix}
\begin{pmatrix}
1 & 1 \\
1 & -1
\end{pmatrix}
= \frac{1}{2}
\begin{pmatrix}
1 & 5 \\
3 & -1 \\
-1 & -1
\end{pmatrix}.
$$
