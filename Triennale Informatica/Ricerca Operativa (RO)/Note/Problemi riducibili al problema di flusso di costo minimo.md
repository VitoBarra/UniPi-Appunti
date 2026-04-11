---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Problemi riducibili al problema di flusso di costo minimo
---
Alcuni problemi classici possono essere formulati come casi particolari del [[Problema del flusso di costo minimo]].

## Caso particolare: problema dei cammini minimi
Il [[Problema del cammini minimi|problema dell'albero dei cammini minimi]] di radice $r$ e un particolare problema di flusso di costo minimo in cui:
- per ogni arco $(i,j) \in A$ si pone $u_{ij}=+\infty$
- il bilancio del nodo radice e $b_r=-(n-1)$
- per ogni nodo $i \neq r$ si pone $b_i=1$
Con questa scelta dei bilanci, il nodo radice invia una unita di flusso verso ciascuno degli altri nodi. Minimizzare il costo totale del flusso equivale quindi a costruire l'albero dei cammini minimi di radice $r$.

## Flusso massimo
Il [[Problema del flusso massimo|problema del flusso massimo]] da $s$ a $t$ su un grafo $(N,A)$ equivale a un problema di flusso di costo minimo sul grafo $(N, A \cup \{(t,s)\})$, ottenuto aggiungendo l'arco $(t,s)$.
La riduzione si costruisce imponendo:
- $b_i=0$ per ogni $i \in N$
- $c_{ij}=0$ per ogni $(i,j) \in A$
- $c_{ts}=-1$
- $u_{ts}=+\infty$
Il problema ottenuto e un problema di circolazione: tutto il flusso che raggiunge $t$ puo tornare in $s$ attraverso l'arco aggiunto $(t,s)$. Poichè questo arco ha costo negativo, minimizzare il costo totale equivale a massimizzare la quantità di flusso che da $s$ arriva a $t$.