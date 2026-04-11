---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---

# Taglio su grafo
---
Dato un [[Graph Theory|grafo]] orientato $G=(N,A)$, un **taglio** e una [[Partizione di un insieme|partizione]] dell'insieme dei nodi in due [[Insiemi Matematici|sottoinsiemi]] $(N',N'')$ tali che:$$
\begin{aligned}
N',N'' &\subseteq N \\
N' \cap N'' &= \emptyset \\
N' \cup N'' &= N
\end{aligned}
$$Gli archi del taglio sono gli archi che hanno un estremo in $N'$ e l'altro in $N''$.

### Taglio orientato

Nel caso di un grafo orientato, fissato un taglio $(N',N'')$, si distinguono:
- gli archi diretti da $N'$ a $N''$
- gli archi diretti da $N''$ a $N'$


### Esempio
![[IMG - taglio su grafo.png]]