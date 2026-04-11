---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---
# Condizione di Bellman
---
Sia $T$ un [[Albero di copertura]] radicato in $r$ e orientato. Per ogni nodo $i\neq r$ esiste un unico cammino da $r$ a $i$ contenuto in $T$; indichiamo con $\pi_i$ il costo di tale cammino, dove $\pi_i$ è il potenziale del nodo $i$ e si calcola ponendo $\pi_j=\pi_i+c_{ij}$ se $pred(j)=i$. 
Allora $T$ è un albero dei cammini minimi se e solo se
$$
\pi_j\leq \pi_i+c_{ij}\qquad \forall (i,j)\notin T.
$$
Cioè, per ogni arco esterno a $T$, il potenziale del nodo di arrivo non può superare il costo del cammino che passa per quell'arco.

## Unicità della soluzione
Se nel [[Graph Theory|grafo]] non esistono cicli orientati di costo $\leq 0$, allora l'albero dei cammini minimi è unico se e solo se tutte le condizioni di Bellman sugli archi esterni a $T$ valgono con disuguaglianza stretta:
$$
\pi_j<\pi_i+c_{ij}\qquad \forall (i,j)\notin T.
$$
Se almeno una di tali disuguaglianze vale con uguaglianza, possono esistere più alberi dei cammini minimi.
