---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Condizionamento della risoluzione dei sistemi lineari
---
si studia il [[Tipi di Errore nel calcolo numerico#Errore Inerente|condizionamento]] del problema della risoluzione di [[Sistemi lineari e lineari  omogenei|Sistemi Lineari]] con le seguenti ipotesi
- $Ax=b$ 
- $A \in \mathbb{F}^{n\times n}$
- $b \in \mathbb{F}^n$
volgiamo studiare il caso in cui la [[Soluzioni di un sistema lineare|soluzione sia unica]]

considerando le possibili perturbazioni prossimo riscrivere  il dato teorico $x = f(A,b)$ e il risultato perturbato come $\tilde x= f(\tilde A,\tilde b)$.
per calcolare l [[Tipi di Errore nel calcolo numerico#Errore Inerente|errore inerente]] dovrei calcolare 
$$\epsilon_{in} = \frac{\tilde x-x}{x}$$ ma essendo $x \ \tilde x$ dei [[Vettori|vettori]] non possiamo a usare la divisione essendo questa _non definita_. usiamo quindi le [[Norme Matriciali e Norme Vettoriali|norme]]  $$\epsilon_{in} = \frac{\|\tilde x-x\|}{\|x\|}$$
### Teorema
supponiamo di non avere perturbazione sulla matrice $A$ quindi $\tilde A = A$ e che $A$ sia [[Matrice inversa|invertibile]], scelta una qualche norma che induce una norma matriciale 
$$\frac{\|\tilde x -x\|}{\|x\|} \leq \|A\|\cdot\|A^{-1}\| \cdot \frac{\|\tilde b-b\| }{\|b\|}$$
$\mu(A) = \|A\|\cdot\|A^{-1}\|$ è il numero di condizionamento 
proprietà:
- $\mu(A) \geq 1$

#### Dimostrazione
$$\begin{array}{}
\tilde x -x = A^{-1}\tilde b- A ^{-1}b = A^{-1}(\tilde b -b) \\
\|\tilde x -x\| = \|A^{-1}(\tilde b -b)\| \le \|A^{-1}\| \cdot \|\tilde b - b\| \\
\|b\| = \|Ax\| \leq \|A\|\cdot \|x\| \implies\\
\|x\| \geq \frac{\|b\|}{\|A\|}
\\ \frac{\|\tilde x -x \|}{\|x\|} \leq \frac{1}{\|x\|} \cdot\|A^{-1}\| \cdot\|\tilde b - b\| \leq \|A\| \cdot \|A^{-1}\| \cdot \frac{\| \tilde b -b\|}{\| b\|}

\end{array}$$