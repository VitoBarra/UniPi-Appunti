---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Programmazione lineare Intera
---

### Definizione

un problema di programmazione lineare intera è un problema nella forma

$$
\begin{cases}
\max c^Tx \\
Ax \leq b \\
x \in \mathbb{Z}^n
\end{cases}
$$

dove $A,b,c$ sono a componenti $\in \mathbb{Z}$ e la regione ammissibile $\Omega$ è limitata

### Teorema

<aside>
💡 Questo probela è NP-Hard

</aside>

### Rilassamento continuo

il problema seguente è un rilassamento continuo del problema di programmazione liniere intera

$$
\begin{cases}
\max c^Tx \\
Ax \leq b
\end{cases}
$$

---

## Relazione problema di programmazione lineare(PLI) e rilassamento continuo (RC)

- il valore ottimo del RC é maggiore o uguale del valore ottimo del PLI
- Se la soluzione ottima del RC é ammissibile per il PLI , allora e ottima anche
per il PLI.

spesso la soluzione ottima di RC non è ammissibile per il PLI

Per risolvere PLI è sufficiente risolvere il suo rilassamento continuo e arrotondare
la soluzione trovata? NO

Per risolvere PLI è sufficiente risolvere il suo rilassamento continuo e scegliere la soluzione ammissibile più vicina rispetto alla distanza euclidea? NO

---



consideriamo i problemi

$$
\begin{cases}
\max c^T \\
x \in \Omega
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \
\begin{cases}
\max c^T \\
x \in conv(\Omega)
\end{cases}
$$

dove $conv(\Omega)$ è l’involucro convesso delle soluzioni ammissibili, cioè il più piccolo
insieme convesso che contiene $\Omega$.

[[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 25.png]]

### Teorema

- $conv(\Omega)$ è un poliedro
- I vertici di $conv(\Omega)$  appartengono a $\Omega$, cioè sono a componenti intere
- I problemi

$$
\begin{cases}
\max c^T \\
x \in \Omega
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \
\begin{cases}
\max c^T \\
x \in conv(\Omega)
\end{cases}
$$

hanno lo stesso valore ottimo e almeno una soluzione ottima comune 

### Corollario

il problema di PLI

$$
\max_{x \in \Omega}c^Tx
$$

è equivalente al problema di PL

$$
\max_{x \in conv(\Omega)}c^Tx
$$

in general é difficile trovare i vincoli che definisco $conv(\Omega)$ ma esistono alcuni problemi particolari si riesce a caratterizzare facilmente $canv(\Omega)$

Sia $Ω = \{x ∈ \mathbb{Z}^n: A x \leq b\}$.  Se $A$ e una matrice totalmente uni-modulare (cioè il
determinante di ogni sua sottomatrice quadrata è 0 oppure 1 oppure −1), allora

$$
conv(\Omega) = \{x ∈ \mathbb{Z}^n: A x \leq b\}
$$

cioè $conv(Ω)$ coincide con la regione ammissibile del rilassamento continuo.


