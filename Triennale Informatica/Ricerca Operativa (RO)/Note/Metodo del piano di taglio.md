---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---
# Metodo del piano di taglio
---
## Diseguaglianza valida
Una disequazione è detta disuguaglianza valida per l'insieme $\Omega$ se $p^Tx\leq p_0\ \forall x\in\Omega$.
### Piano di taglio
Un piano di taglio è una disuguaglianza valida $p^Tx\leq p_0$ per $\Omega$ tale che $p^T\bar{x}>p_0$, dove $\bar{x}$ è l'ottimo del rilassamento continuo.
## Metodo del piano di taglio
Se $P$ è la regione ammissibile del rilassamento continuo e la soluzione ottima $\bar{x}$ di $\max_{x\in P}c^Tx$ appartiene a $\Omega$, allora $\bar{x}$ è ottima anche per $\max_{x\in\Omega}c^Tx$. Altrimenti si costruisce un piano di taglio $p^Tx\leq p_0$ in modo da tagliare fuori $\bar{x}$ e si risolve il nuovo problema di [[Programmazione lineare|PL]]:
$$
\begin{cases}
\max c^Tx \\
x\in P \\
p^Tx\leq p_0
\end{cases}
$$
## Piani di taglio di Gomory
Supponiamo che il problema di [[Programmazione lineare Intera|PLI]] sia nella forma
$$
\begin{cases}
\max c^Tx \\
Ax=b \\
x\geq 0 \\
x\in\mathbb{Z}^n
\end{cases}
$$
e che $\bar{x}$ sia una soluzione di base ottima del rilassamento continuo, relativa alla [[Basi e vertici|base]] $B$. Poniamo $A=(A_B,A_N)$, $\bar{x}=\begin{pmatrix}x_B\\x_N\end{pmatrix}$, $\tilde{A}=A_B^{-1}A_N$, $\tilde{b}=\bar{x}_B$. Se esiste un indice $r\in B$ tale che $\tilde{b}_r\notin\mathbb{Z}$, allora
$$
\sum_{j\in N}\{\tilde{a}_{rj}\}x_j\geq \{\tilde{b}_r\}
$$
è un piano di taglio di Gomory, dove $\{\cdot\}$ indica la parte frazionaria.

## Dimostrazione del taglio di Gomory
Fissiamo $x\in\Omega$. Dalla relazione $Ax=A_Bx_B+A_Nx_N=b$ segue $x_B=A_B^{-1}b-A_B^{-1}A_Nx_N=\tilde{b}-\tilde{A}x_N$. Indicando con $\tilde{x}=x_B$, la componente $r$-esima soddisfa
$$
\tilde{x}_r=\tilde{b}_r-\sum_{j\in N}\tilde{a}_{rj}x_j.
$$
Scomponendo in parte intera e parte frazionaria si ottiene
$$
\tilde{x}_r=\lfloor \tilde{b}_r\rfloor+\{\tilde{b}_r\}-\sum_{j\in N}\lfloor \tilde{a}_{rj}\rfloor x_j-\sum_{j\in N}\{\tilde{a}_{rj}\}x_j.
$$
Di conseguenza
$$
\sum_{j\in N}\{\tilde{a}_{rj}\}x_j-\{\tilde{b}_r\}=\lfloor \tilde{b}_r\rfloor-\sum_{j\in N}\lfloor \tilde{a}_{rj}\rfloor x_j-\tilde{x}_r\in\mathbb{Z}.
$$
Inoltre vale
$$
\sum_{j\in N}\{\tilde{a}_{rj}\}x_j-\{\tilde{b}_r\}\geq -\{\tilde{b}_r\}>-1.
$$
Un numero intero maggiore di $-1$ è non negativo, quindi
$$
\sum_{j\in N}\{\tilde{a}_{rj}\}x_j\geq \{\tilde{b}_r\}.
$$
Questa disuguaglianza è quindi valida per $\Omega$. Inoltre non è soddisfatta da $\bar{x}$, perché per la soluzione di base ottima vale $\bar{x}_N=0$ e dunque $0=\sum_{j\in N}\{\tilde{a}_{rj}\}\bar{x}_j<\{\tilde{b}_r\}$. La disuguaglianza ottenuta è quindi un piano di taglio. ![[IMG - visualizzazione tagli di gomory.png]]
