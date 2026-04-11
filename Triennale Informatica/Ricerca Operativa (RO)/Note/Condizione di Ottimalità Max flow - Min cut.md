---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---

# Condizione di Ottimalità Max flow - Min cut
---

### Condizione sufficiente di ottimalità Teorema (max flow - min cut)
Se esistono un [[Flusso su grafo|flusso]] ammissibile $x$ e un [[Taglio su grafo|taglio]] ammissibile $(N_s,N_t)$ tali che$$x(N_s,N_t)=u(N_s,N_t),$$allora $x$ è un flusso di valore massimo e $(N_s,N_t)$ è un taglio di capacità minima.


### Condizione necessaria e sufficiente di ottimalità
Sia $x$ un [[Flusso su grafo|flusso]] ammissibile. Allora $x$ è un flusso di valore massimo se e solo se non esiste un [[Cammino aumentante|cammino aumentante]] rispetto ad $x$.

**Dimostrazione**
Se esiste un [[Cammino aumentante|cammino aumentante]] rispetto ad $x$, allora spedendo lungo tale cammino un flusso che rispetta le capacità residue si ottiene un altro flusso ammissibile $x'$ di valore maggiore rispetto ad $x$. Pertanto $x$ non è di valore massimo.

Se non esiste un [[Cammino aumentante|cammino aumentante]] rispetto ad $x$, allora si può definire il taglio $(N_s,N_t)$, dove
$$
\begin{array}{}
N_s  & = &  \{ i \in N : \text{esiste in } G(x) \text{ un cammino orientato da } s \text{ a } i \} \\
N_t  & = &  \{ i \in N : \text{non esiste in } G(x) \text{ un cammino orientato da } s \text{ a } i \}
\end{array}
$$
Il [[Taglio su grafo|taglio]] è ammissibile perché $s \in N_s$ e $t \in N_t$. Inoltre, dalla definizione del taglio si ottiene che$$
x(N_s,N_t)=u(N_s,N_t)$$Quindi, per il **teorema max flow - min cut**, il flusso $x$ è di valore massimo e $(N_s,N_t)$ è un taglio di capacità minima.
