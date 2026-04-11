---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---

# Pseudoflusso
---
Uno **pseudoflusso** $x$ è un [[Flusso su grafo|flusso]] che rispetta i vincoli di capacità degli archi$$0 \leq x_{ij} \leq u_{ij}$$ma non necessariamente i vincoli di bilancio dei nodi.

Se $x$ è uno **pseudoflusso**, allora$$e_x(i) = \sum_{(j,i) \in A} x_{ji} - \sum_{(i,j) \in A} x_{ij} - b_i$$è chiamato lo sbilanciamento del nodo $i$ rispetto a $x$.

Indichiamo con:$$E_x = \{ i \in N : e_x(i) > 0 \}$$l'insieme dei nodi con eccesso di [[Flusso su grafo|flusso]],$$D_x = \{ i \in N : e_x(i) < 0 \}$$l'insieme dei nodi con difetto di [[Flusso su grafo|flusso]],$$g(x) = \sum_{i \in E_x} e_x(i)$$lo sbilanciamento complessivo di $x$.


## Ammissibilità
Uno **pseudoflusso** $x$ è ammissibile, cioè rispetta anche i vincoli di bilancio, se e solo se $E_x = D_x = \emptyset$, equivalentemente se e solo se $g(x)=0$.

## Minimalità
Uno **pseudoflusso** $x$ è detto minimale se ha **costo minimo** tra tutti gli **pseudoflussi** aventi lo stesso vettore di sbilanciamenti $e_x$.

### Teorema
Uno [[Pseudoflusso|pseudoflusso]] $x$ è minimale se e solo se nel [[Grafo residuo|grafo residuo]] $G(x)$ non esistono [[Ciclo aumentante|cicli aumentanti]] di costo negativo.
