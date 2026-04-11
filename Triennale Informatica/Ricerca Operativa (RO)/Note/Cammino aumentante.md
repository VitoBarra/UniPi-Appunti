---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Cammino aumentante
---
Dato un [[Flusso su grafo|flusso]] ammissibile $x$, un **cammino aumentante** rispetto ad $x$ è un cammino orientato da $s$ a $t$ nel [[Grafo residuo|grafo residuo]] $G(x)$.

Un **cammino aumentante** individua un percorso lungo il quale è possibile aumentare il valore del flusso.
La quantità massima che può essere inviata lungo tale cammino è pari alla minima capacità residua degli archi del cammino.

Un cammino aumentante nel [[Grafo residuo|grafo residuo]] non è necessariamente un cammino orientato nel grafo iniziale, perché può utilizzare anche archi all'indietro che rappresentano la possibilità di ridurre parte del flusso già inviato.