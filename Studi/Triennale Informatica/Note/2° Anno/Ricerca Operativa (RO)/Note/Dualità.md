---
Subject: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Dualità
---

## Problema primale

un problema di [[Programmazione lineare|PL]] in forma canonica è detto primale nella forma

$$
\begin{cases}
\max c^Tx \\
x \in P =\{x \in \mathbb{R}^n \ | \ Ax \leq b\}
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
(\mathcal{P})
$$

## Problema duale

il problema duale di un altro problema di PL  è definito come

$$
\begin{cases}
\min y^Tb \\
y \in D = \{y \in \mathbb{R}^m \ |\ y^TA = c^T, y \geq 0 \}
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ (\mathcal{D})
$$

|  | Primale | Duale |
| --- | --- | --- |
| Obiettivo | max  | min |
| Variabili  | n | m |
| Vincoli | m | n |

### Esempio

dato il problema

$$
\begin{cases}
\max 4x_1 +5x_2 \\
x_1 \leq 1 \\
x_2 \leq 2 \\
x_1 +x_2 \leq 3
\end{cases}
\ \ \ \ \ \
A=
\begin{pmatrix}
1 & 0 \\
0 & 1 \\
1 & 1
\end{pmatrix}
b=
\begin{pmatrix}
1 \\
2 \\
3
\end{pmatrix}
c=
\begin{pmatrix}
4 \\
5 \\
\end{pmatrix}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
(\mathcal{P})
$$

il suo duale è

$$
\begin{cases}
\min y_i +2y_2 +3y_3 \\
y_1 +y_3 = 4 \\
y_2 + y_3 =5 \\
y \geq 0
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ (\mathcal{D})
$$
