---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Condizione di ottimalità sui tagli
---

>[!tip] #### Osservazione
>Se da un albero di copertura $T$ viene eliminato un arco $(u,v) \in T$, si formano 2 componenti connesse $N'$ e $N''$, e quindi un taglio $(N',N'')$ tale che $(u,v)$ é l unico arco del taglio che appartiene a $T$.

### Teorema

Sia $T$ un [[Albero di copertura]].

$T$ è un albero di copertura di costo minimo se e solo se per ogni carco $(u,v) \in T$ si ha $c_{uv} \leq c_{ij}$ per ogni arco $(i,j)$ del taglio ottenuto eliminando da $T$ l arco $(u,v)$

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2 1.png]]

![[Raccolta UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 3.png]]
