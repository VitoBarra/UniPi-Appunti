---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Algoritmo di programmazione dinamica per trovare cammini minimi
---
Se il [[Graph Theory|grafo]] $(N,A)$ è aciclico, cioè non esistono cicli orientati, allora un [[Albero di cammini minimi|albero dei cammini minimi]] di radice $r$ si può trovare utilizzando un algoritmo di [[Programmazione Dinamica|programmazione dinamica ]].

Prima di tutto, è necessario fare un ordinamento topologico dei nodi, cioè numerare i nodi in modo che

$$
(i,j) \in A \Longrightarrow i < j.
$$

Tale ordinamento può essere effettuato con il seguente algoritmo:
1. Assegno 1 alla radice $r$, elimino dal grafo $r$ e tutti gli archi uscenti da $r$. Pongo $k=2$.
2. Assegno $k$ ad un nodo $i$ che non ha archi entranti.
3. Elimino il nodo $i$ e tutti gli archi uscenti da $i$.
4. Se il grafo è vuoto, allora stop; altrimenti $k=k+1$ e torna al passo 2.

Dopo aver definito un ordinamento topologico dei nodi, l'algoritmo di [[Programmazione Dinamica|programmazione dinamica]] per trovare un [[Albero di cammini minimi|albero dei cammini minimi]] di radice 1 è il seguente:
- Poni $\pi_1 = 0$.
- Per ogni nodo $j = 2,\dots,n$:

$$
\text{trova } u = \arg \min_{i<j} \{\pi_i + c_{ij}\}
$$
$$
\text{poni } p_j = u, \qquad \pi_j = \pi_u + c_{uj}
$$
Dove $p$ è il vettore dei predecessori dei nodi che rappresenta l'albero e $\pi$ è il corrispondente vettore dei potenziali dei nodi, come nella [[Condizione di Bellman|condizione di Bellman]].
