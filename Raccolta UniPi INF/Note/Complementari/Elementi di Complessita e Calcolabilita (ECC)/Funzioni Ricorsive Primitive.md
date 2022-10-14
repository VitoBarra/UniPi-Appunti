---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Funzioni Ricorsive Primitive
---
la classe delle funzioni ricorsive primitive è la minima classe di [[Funzioni]] $\mathcal{C}: \N^n \rightarrow \N$ con $n\geq 0$ che contengono

$$
\begin{matrix}
I & Zero & \lambda x_1,\dots,x_k.0 & k\geq 0 \\
II & Successore & \lambda x.x+1 \\
III & Identita & \lambda x_1,\dots,x_k.x_i & 1\leq i\leq k \\
\end{matrix}
$$
dette anche schemi primitivi di base, e che è chiusa per:
$$

\begin{matrix}
IV & Composizione \\
V & \text{Ricorsione primitva}  \\
\end{matrix}
$$
![[Pasted image 20221014022815.png]]
