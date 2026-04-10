---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
topic:
---

# Matrice Associata
---
sia $f$ una [[Applicazioni Lineari|applicazione lineare]], la [[Matrici|matrice]] associata e una matrice definita nel modo seguente.

Sia

$$
f : V \to W
$$

un'applicazione lineare fra spazi vettoriali definiti su $\mathbb{K}$. Siano inoltre

$$
\mathcal{B} = \{v_1, \dots, v_n\},
\qquad
\mathcal{C} = \{w_1, \dots, w_m\}
$$

due basi rispettivamente di $V$ e di $W$. Sappiamo che

$$
f(v_1) = a_{11}w_1 + \cdots + a_{m1}w_m,
$$

$$
\vdots
$$

$$
f(v_n) = a_{1n}w_1 + \cdots + a_{mn}w_m,
$$

per qualche insieme di coefficienti $a_{ij} \in \mathbb{K}$. Definiamo la matrice associata a $f$ nelle basi $\mathcal{B}$ e $\mathcal{C}$ come la matrice $m \times n$

$$
A = (a_{ij})
$$

che raggruppa questi coefficienti, e la indichiamo con il simbolo

$$
A = [f]_{\mathcal{C}}^{\mathcal{B}}.
$$

Esempi:

**Esempio 4.3.2.** Consideriamo l'applicazione lineare

$$
f : \mathbb{R}_2[x] \to \mathbb{R}^2,
\qquad
f(p) = \begin{pmatrix}p(2)\\p(-2)\end{pmatrix}
$$

che assegna ad ogni polinomio i suoi valori in $2$ e in $-2$. Scriviamo la matrice associata a $f$ nelle basi canoniche

$$
\mathcal{C}' = \{1, x, x^2\}
$$

di $\mathbb{R}_2[x]$ e

$$
\mathcal{C} = \{e_1, e_2\}
$$

di $\mathbb{R}^2$. Calcoliamo:

$$
f(1) = \begin{pmatrix}1\\1\end{pmatrix},
\qquad
f(x) = \begin{pmatrix}2\\-2\end{pmatrix},
\qquad
f(x^2) = \begin{pmatrix}4\\4\end{pmatrix}.
$$

Quindi la matrice associata e

$$
[f]_{\mathcal{C}}^{\mathcal{C}'} =
\begin{pmatrix}
1 & 2 & 4 \\
1 & -2 & 4
\end{pmatrix}.
$$

Se in arrivo prendiamo la base

$$
\mathcal{B} = \left\{ \begin{pmatrix}1\\-1\end{pmatrix}, \begin{pmatrix}0\\1\end{pmatrix} \right\}
$$

invece della canonica $\mathcal{C}$, allora dobbiamo anche calcolare le coordinate di ciascun vettore immagine rispetto a $\mathcal{B}$. Risolvendo dei semplici sistemi lineari troviamo

$$
f(1) = \begin{pmatrix}1\\1\end{pmatrix} = \begin{pmatrix}1\\-1\end{pmatrix} + 2\begin{pmatrix}0\\1\end{pmatrix},
$$

$$
f(x) = \begin{pmatrix}2\\-2\end{pmatrix} = 2\begin{pmatrix}1\\-1\end{pmatrix} + 0\begin{pmatrix}0\\1\end{pmatrix},
$$

$$
f(x^2) = \begin{pmatrix}4\\4\end{pmatrix} = 4\begin{pmatrix}1\\-1\end{pmatrix} + 8\begin{pmatrix}0\\1\end{pmatrix}
$$

e la matrice associata diventa quindi

$$
[f]_{\mathcal{B}}^{\mathcal{C}'} =
\begin{pmatrix}
1 & 2 & 4 \\
2 & 0 & 8
\end{pmatrix}.
$$

**Esempio 4.3.3.** Consideriamo l'applicazione lineare

$$
f : \mathbb{C}^2 \to \mathbb{C}^3,
\qquad
f\begin{pmatrix}x\\y\end{pmatrix} = \begin{pmatrix}x-y\\2x\\y\end{pmatrix}.
$$

La matrice associata a $f$ rispetto alle basi canoniche e semplicemente quella dei coefficienti:

$$
\begin{pmatrix}
1 & -1 \\
2 & 0 \\
0 & 1
\end{pmatrix}.
$$

Se invece come basi prendiamo in partenza

$$
v_1 = \begin{pmatrix}1\\1\end{pmatrix},
\qquad
v_2 = \begin{pmatrix}1\\-1\end{pmatrix}
$$

e in arrivo

$$
w_1 = \begin{pmatrix}1\\1\\0\end{pmatrix},
\qquad
w_2 = \begin{pmatrix}0\\1\\1\end{pmatrix},
\qquad
w_3 = \begin{pmatrix}1\\0\\1\end{pmatrix},
$$

allora per calcolare la matrice associata dobbiamo determinare le coordinate di $f(v_1)$ e $f(v_2)$ rispetto alla base $w_1, w_2, w_3$. Risolvendo dei sistemi lineari troviamo

$$
f(v_1) = \begin{pmatrix}0\\2\\1\end{pmatrix} = \frac{1}{2}\begin{pmatrix}1\\1\\0\end{pmatrix} + \frac{3}{2}\begin{pmatrix}0\\1\\1\end{pmatrix} - \frac{1}{2}\begin{pmatrix}1\\0\\1\end{pmatrix},
$$

$$
f(v_2) = \begin{pmatrix}2\\2\\-1\end{pmatrix} = \frac{5}{2}\begin{pmatrix}1\\1\\0\end{pmatrix} - \frac{1}{2}\begin{pmatrix}0\\1\\1\end{pmatrix} - \frac{1}{2}\begin{pmatrix}1\\0\\1\end{pmatrix}.
$$

Quindi la matrice associata a $f$ rispetto alle basi $v_1, v_2$ e $w_1, w_2, w_3$ e

$$
[f]_{w_1,w_2,w_3}^{v_1,v_2} =
\begin{pmatrix}
\frac{1}{2} & \frac{5}{2} \\
\frac{3}{2} & -\frac{1}{2} \\
-\frac{1}{2} & -\frac{1}{2}
\end{pmatrix}
= \frac{1}{2}
\begin{pmatrix}
1 & 5 \\
3 & -1 \\
-1 & -1
\end{pmatrix}.
$$

### Proprietà:

Abbiamo scoperto come caratterizzare qualsiasi applicazione lineare, fra spazi di dimensione finita, come una matrice. Adesso mostriamo una proprieta notevole di questa caratterizzazione.

Dalla matrice associata possiamo facilmente calcolare l'immagine di qualsiasi vettore. Sia $f : V \to W$ un'applicazione lineare e siano

$$
\mathcal{B} = \{v_1, \dots, v_n\},
\qquad
\mathcal{C} = \{w_1, \dots, w_m\}
$$

basi di $V$ e di $W$.

**Proposizione 4.3.4.** Per ogni $v \in V$ troviamo

$$
[f(v)]_{\mathcal{C}} = [f]_{\mathcal{C}}^{\mathcal{B}} [v]_{\mathcal{B}}.
$$
