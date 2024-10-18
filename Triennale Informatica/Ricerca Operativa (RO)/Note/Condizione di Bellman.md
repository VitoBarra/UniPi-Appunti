---
Course: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Condizione di Bellman
---

### Definizione

se $T$ è un [[Albero di copertura]] radicato in $r$ e orientato, allora esiste un unico comino da r ad ogni nodi $i \not=r$.

indichiamo con $\pi_i$ detto potenziale di i il costo di tale commino

Per calcolare i potenziali $\pi$ basta fare una visita del albero $T$ e porre $\pi_j = \pi_i +c_{ij}$

se $pred(j)=i$

## *Condizioni di Bellman*

Sia $T$ un albero di copertura radicato in $r$ e orientato e $\pi$ il corrispondente vettore dei potenziali dei nodi.

$T$ è un albero di cammini minimi $\iff$ $\pi_j \leq \pi_i +c_{ij} \ \ \ \ \ \forall(i,j) \not\in T$

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 7.png]]
![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 1 3.png]]

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 2 3.png]]

## Unicità della soluzione

![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 3 2.png]]
