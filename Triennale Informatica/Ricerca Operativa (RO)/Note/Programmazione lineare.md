---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags:
  - RO
---

# Programmazione lineare
---
nella **programmazione lineare** il [[Modelli Matematici|Modello]] matematico di un problema viene espresso come una funzione $c$ da minimizzare o massimizzare e da une un set di $n$ equazioni detti _Vincoli_. questo sistema si puo anche riscrivere in forma [[Matrici|Matriciale]]

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 14.png]]

La regione ammissibile di ogni problema di un [PL](app://obsidian.md/Programmazione%20lineare) è un [Poliedro](app://obsidian.md/Poliedro).

### Rappresentato dal modello

Variabili decisionali:
$x_L$ = numero di ettari da coltivare a lattuga
$x_P$ = numero di ettari da coltivare a patate

Modello di programmazione lineare:

$$
\begin{cases}
\max 3000x_L+5000x_P \\
x_L+x_p \leq 12 \\
x_L \leq 10 \\
x_P \leq 6 \\
x_L+2x_P \leq 16 \\
x_L \geq 0 \\
x_P \geq 0 \\

\end{cases}
$$

bisogna prima riscriverlo in forma canonica riscrivendo tutte le equazioni nella forma $x \leq b$ per poi poter essere riscritto in forma [[Matrici|matriciale]]

$$
\begin{cases}
\max 3x_L+5x_P \\
x_L+x_p \leq 12 \\
x_L \leq 10 \\
x_P \leq 6 \\
x_L+2x_P \leq 16 \\
-x_L \leq 0 \\
-x_P \leq 0 \\

\end{cases}
$$

$$
\begin{cases}
\max \ c^Tx \\
Ax \leq b
\end{cases}

$$

$$
x =
\begin{pmatrix}
x_L \\
 x_P
\end{pmatrix}
\ \ \
A=
\begin{pmatrix}
1 \ \ \ \ \ \ \ \ 1\\
1 \ \ \ \ \ \ \ \ 0\\
0 \ \ \ \ \ \ \ \ 1\\
1 \ \ \ \ \ \ \ \ 2\\
-1 \ \ \ \ \ \ 0\\
0 \ \ \ \ -1\\
\end{pmatrix}
\ \ \
b=
\begin{pmatrix}
12 \\
10 \\
6 \\
16 \\
0 \\
0 \\
\end{pmatrix}
\ \ \
c=
\begin{pmatrix}
3 \\
5 \\
\end{pmatrix}

$$

- $m$ = numero di vincoli
- $n$ = numero di variabili
- $A$ matrice $m \times n$
- $b$ vettore con $m$ componenti
- $c$ vettore con $n$ componenti

