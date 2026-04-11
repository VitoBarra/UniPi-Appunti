---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Problemi riducibili al Problema di flusso massimo
---
Un importante problema riducibile al [[Problema del flusso massimo]] e il problema dell'accoppiamento di massima cardinalità in un [[Grafo bipartito|grafo bipartito]].

## Accoppiamento di massima cardinalità

Sia $(N,A)$ un grafo bipartito con partizione dei vertici $O \cup D = N$. Il problema dell'accoppiamento di massima cardinalità su $(N,A)$ e equivalente a un problema di flusso massimo da $s$ a $t$ su un grafo $(N',A')$, dove:
- $N' = N \cup \{s,t\}$
- $A' = A \cup \{(s,i) : i \in O\} \cup \{(j,t) : j \in D\}$
- le capacita superiori di tutti gli archi sono uguali a $1$
Con questa costruzione, ogni cammino da $s$ a $t$ che attraversa un arco del grafo bipartito individua una coppia ammissibile dell'accoppiamento. Di conseguenza, il valore del flusso massimo coincide con la cardinalità massima dell'accoppiamento.
![[IMG - riduzione accoppiamento a flusso massimo.png]]
