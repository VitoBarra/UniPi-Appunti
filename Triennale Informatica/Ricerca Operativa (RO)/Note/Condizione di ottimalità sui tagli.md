---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---


# Condizione di ottimalità sui tagli
---

### Teorema

**Sia** $T$ un [[Albero di copertura]].
**allora** $T$ è un albero di copertura di costo minimo se e solo se per ogni carco $(u,v) \in T$ si ha $c_{uv} \leq c_{ij}$ per ogni arco $(i,j)$ del [[Taglio su grafo|taglio]] ottenuto eliminando da $T$ l arco $(u,v)$

>[!tip] #### Osservazione
>Se da un albero di copertura $T$ viene eliminato un arco $(u,v) \in T$, si formano 2 componenti connesse $N'$ e $N''$, e quindi un [[Taglio su grafo|taglio]] $(N',N'')$ tale che $(u,v)$ é l unico arco del taglio che appartiene a $T$.