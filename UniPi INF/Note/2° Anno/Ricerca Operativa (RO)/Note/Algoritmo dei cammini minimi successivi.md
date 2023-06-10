---
type: nota
course: Ricerca Operativa
topic: 
tags: RO Algoritmo 
---

Prev: [[Ricerca Operativa (RO)]]

# Algoritmo dei cammini minimi successivi
---

![[UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 9.png]]

### *Teorema*
Se le capacita ed i bilanci  degli archi di un [[Grafo|grafo]] sono numeri interi, allora l [[Algoritmi|algoritmo]] trova una soluzione ottima dopo un numero finito di iterazioni

### dimostrazione

- ad ogni iterazione $x$  ha componenti intere e quindi anche lo sbilanciamento complessivo $g(x)$ è intero. Poiché $g(x)$ diminuisce ad ogni iterazione di almeno una unita, l algoritmo si ferma dopo un numero finito di iterazioni
- Al prima iterazione $x$ è uno pseudoflusso minimale perché in $G(x)$ non ci sono archi di costo negativo
- Poiché ad ogni iterazioni si spedisce flusso lungo un cammino aumentante di costo minimo da un nodo di $E_x$ ad un nodo di $D_x$, il nuovo pseudoflusso ottenuto rimane minimale
- Al ultima iterazioni lo pseudoflusso minimale é ammissibile e quindi è un flusso di costo minimo

### *Algoritmo*

1. per ogni $(i,j) \in A$ poni $x_{ij}=\begin{cases}0  \ \ \ \ \ \ \ \ se \ \ c_{ij}\geq 0\\u_{ij}  \ \ \ \ \ se \ \ c_{ij}< 0\\\end{cases}$
2. Se $E_x=\emptyset$ allora stop $x$ è ottimo
3. Aggiungi a $G(x)$ un nodo $r$ e gli archi $(r,i)$ per ogni $i\in E_x$ con costo $c_{ri} =0$ e capacita residua $r_{ri} = +\infty$
Trova in $G(x)$ un albero dei cammini minimi $T$ di radice $r$.
4. Trova $t =\arg\min_{i\in D_x}\pi_i$(nodo di $D_x$ con potenziale minimo)
se $\pi_t = \infty$ allora stop (non esistono flussi ammissibili)
5. Indica con $P$ il cammino da $r$ a $t$ contenuto nel albero $T$
($P$ passa per un nodo $s \in E_x$)
Calcola $\delta = \min\{e_x(s),-e_x(t),\min\{r_{ij}:(i,j)\in P\}\}$ (max quantità da spedire lungo $P$)
6. aggiorna $x$ spedendo $\delta$ unita di flusso lungo il cammino $P$ e torna al passo 2.

![[UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 4.png]]

![[UniPi INF/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2 4.png]]
