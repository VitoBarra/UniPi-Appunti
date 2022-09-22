---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Basi e vertici
---
# Basi

Una base è un insieme $B$ di $n$ indici di riga tali che la sottomatrice $A_B$ (formata dalle righe $A_i$  con $i \in B$) sia [[Matrice inversa|invertibile]], cioè $det(A_B ) \not= 0$. Indichiamo con $N$ l’insieme degli indici non in base:

$$
A=
\begin{pmatrix}
A_B \\ A_N
\end{pmatrix}
\ \ \ \ \ \
b=
\begin{pmatrix}
b_B \\ b_N
\end{pmatrix}

$$

### Soluzione di base Primale

Data una base $B$, il vettore

$$
\overline{x} = A_B^{−1} b_B
$$

è  chiamato soluzione di base primale.

Tipologie di soluzioni di base primale $\overline{x}$:

- ammissibile se $A_N \overline{x} \leq b_N$ cioè tutti i vincoli non di base sono soddisfatti
- non ammissibile se $\exists i \in N \ | \ A_i \overline{x}> b_i$  cioè almeno un vincolo non di base è violato
- degenere se $\exists i \in N \ | \   A_i \overline{x} = b_i$  cioè almeno un vincolo non di base è
attivo in $\overline{x}$
- non degenere se $\forall i \in N \ | \   A_i \overline{x} \not= b_i$  cioè nessun vincolo non di base è
attivo in $\overline{x}$

### Soluzione di base duale

Data una base $B$ , il vettore

$$
\overline{y} =
\begin{pmatrix}
\overline{y}_B \\
\overline{y}_N
\end{pmatrix}
\ \ \ \ \ \
\text{ dove }
\ \ \ \
\overline{y}_B^T = c^TA_B^{-1},
\ \ \ \
\overline{y}_N =0
$$

 è detto soluzione di base duale

Tipologie di soluzioni di base primale $\overline{y}$:

- ammissibile se $\overline{y}_b \geq 0$
- non ammissibile se $\exists i \in B\ | \ \overline{y}_i<0$
- degenere se $\exists i \in B \ | \ \overline{y}_i = 0$
- non degenere se $\forall i \in B \ | \  \overline{y}_i \not= 0$
