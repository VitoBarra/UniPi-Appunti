---
Subject: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Condizionamento della risoluzione dei sistemi lineari
---
si studia il [[Tipi di Errore nel calcolo numerico#Errore Inerente|condizionamento]] del problema della risoluzione di [[Sistemi lineari e lineari omogenei|Sistemi Lineari]] con le seguenti ipotesi
- $Ax=b$ 
- $A \in \mathbb{F}^{n\times n}$
- $b \in \mathbb{F}^n$
volgiamo studiare il caso in cui la [[Soluzioni di un sistema lineare|soluzione sia unica]]

considerando le possibili perturbazioni prossimo riscrivere  il dato teorico $x = f(A,b)$ e il risultato perturbato come $\tilde x= f(\tilde A,\tilde b)$.
per calcolare l [[Tipi di Errore nel calcolo numerico#Errore Inerente|errore inerente]] dovrei calcolare 
$$\epsilon_{in} = \frac{\tilde x-x}{x}$$ma essendo $x \ \tilde x$ dei [[Vettori|vettori]] non possiamo utilizzare la divisione essendo questa _non definita_ per i vettori. usiamo quindi le [[Norme Matriciali e Norme Vettoriali|norme]]  $$\epsilon_{in} = \frac{\|\tilde x-x\|}{\|x\|}$$
### Teorema
_Sia_ $\tilde A = A$ e $\|\cdot\|_{v}$ una qualche [[Norme Matriciali e Norme Vettoriali|norma]] che _induce una norma matriciale_ $\|\cdot\|_{m}$
_Se_  $A$ è [[Matrice inversa|invertibile]] 
_Allora_ abbiamo che
$$\frac{\|\tilde x -x\|}{\|x\|} \leq \mathcal{K}(A) \cdot \frac{\|\tilde b-b\| }{\|b\|}$$
$\mathcal{K}(A) = \|A\|\cdot\|A^{-1}\|$ è il numero di condizionamento 
##### Dimostrazione
_sia_ $e=[b_{1}\delta_{1},\dots,b_{n}\delta_{n}]$ il vettore delle perturbazioni di $b$
_abbiamo che_  $\tilde{b} = b+e$ e  dalla definizione di sistema lineare abbiamo $Ax=b\implies x=A^{-1}b$
e quindi 
$$\begin{array}{}
\tilde x -x   & = &   A^{-1}\tilde b- A^{-1}b  & = \\
A^{-1}(\tilde b-b) & =  & A^{-1}e
\end{array}$$
che valutando in norme diventa
$$\|\tilde{x}-x\|_{v}=\|A^{-1}e\|_{v} \leq \|A^{-1}\|_{m}\|e\|_{v}$$
dove $\|\cdot\|_{m}$ è la _[[Norme Matriciali e Norme Vettoriali|norma matriciale indotta]]_ da $\|\cdot\|_{v}$ e possiamo cosi usare il [[Teorema compatibilità delle norme|teorema delle compatibilità]] delle norme

in più abbiamo 
$$\begin{array}{}
\|b\|_{v} & = & \|Ax\|_{v} & \leq & \|A\|_{m}\|x\|_{v}   & \implies\\
 &  & \|x\|_{v}  & \geq &  \cfrac{\|b\|_{v}}{\|A\|_{m}}
\end{array} $$
e unendo le due relazioni possiamo scrivere
$$\frac{\|\tilde x -x\|}{\|x\|} \leq \frac{\|A^{-1}\|\|e\| }{\cfrac{\|b\|}{\|A\|}}=\|A\|\cdot\|A^{-1}\| \cdot \frac{\|e\| }{\|b\|}$$

#### Proprietà di $\mathcal{K}(A)$:
questo è sempre $\mathcal{K}(A)\geq1$ siccome
$$1=\|I_{n}\|=\|AA^{-1}\| \ \leq \|A\|\|A^{-1}\| =\mathcal{K}(A)$$
