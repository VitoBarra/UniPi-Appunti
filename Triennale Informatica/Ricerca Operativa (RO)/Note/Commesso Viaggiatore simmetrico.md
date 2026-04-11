---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Commesso Viaggiatore simmetrico
---
Il problema del **commesso viaggiatore simmetrico** consiste nel determinare un [[Ciclo Hamiltoniano|ciclo hamiltoniano]] di costo minimo su un [[Graph Theory|grafo completo]] non orientato, in cui il costo $c_{ij}$ rappresenta il costo di attraversamento dell'arco $\{i,j\}$.

## Modello 1
Si introducono variabili binarie:

$$
x_{ij} =
\begin{cases}
1 & \text{se } \{i,j\} \text{ appartiene al ciclo hamiltoniano} \\
0 & \text{altrimenti}
\end{cases}
\qquad i<j
$$

La formulazione e:

$$
\begin{cases}
\min \sum\limits_{i\in N}\sum\limits_{j\in N,\, j>i} c_{ij}x_{ij} \\
\sum\limits_{j\in N,\, j>i} x_{ij} + \sum\limits_{j\in N,\, j<i} x_{ji} = 2 \qquad \forall i \in N \\
\sum\limits_{i\in S}\sum\limits_{j\notin S,\, j>i} x_{ij} + \sum\limits_{i\notin S}\sum\limits_{j\in S,\, j>i} x_{ij} \geq 1 \qquad \forall S \subset N,\ |S|\geq 1 \\
x_{ij} \in \{0,1\} \qquad \forall i,j \in N,\ i<j
\end{cases}
$$

I vincoli impongono che:

- ogni nodo abbia grado $2$
- non esistano sottocicli separati dal resto del grafo

## Modello 2
Una formulazione equivalente utilizza ancora variabili binarie $x_{ij}$, ma i vincoli di eliminazione dei sottocicli sono scritti nella forma:
$$
\sum\limits_{i\in S}\sum\limits_{j\in S,\, j>i} x_{ij} \leq |S|-1 \qquad \forall S \subset N,\ |S|\geq 3
$$

La formulazione completa diventa:
$$
\begin{cases}
\min \sum\limits_{i\in N}\sum\limits_{j\in N,\, j>i} c_{ij}x_{ij} \\
\sum\limits_{j\in N,\, j>i} x_{ij} + \sum\limits_{j\in N,\, j<i} x_{ji} = 2 \qquad \forall i \in N \\
\sum\limits_{i\in S}\sum\limits_{j\in S,\, j>i} x_{ij} \leq |S|-1 \qquad \forall S \subset N,\ |S|\geq 3 \\
x_{ij} \in \{0,1\} \qquad \forall i,j \in N,\ i<j
\end{cases}
$$

Anche in questo caso:
- i vincoli di grado impongono che ogni nodo abbia grado $2$
- i vincoli su $S$ eliminano i sottocicli

## Rilassamento mediante r-albero

Fissato un nodo $r$, un **r-albero** e un insieme di $n$ archi tale che:
- due archi sono incidenti nel nodo $r$
- i rimanenti $n-2$ archi formano un [[Problema del albero di copertura costo minimo|albero di copertura]] sui nodi diversi da $r$
Ogni ciclo hamiltoniano e un r-albero. Di conseguenza, il problema del r-albero di costo minimo e un rilassamento del problema del commesso viaggiatore simmetrico.

Questo rilassamento e facile da risolvere, perche basta determinare:
- i due archi di costo minimo incidenti nel nodo $r$
- un [[Problema del albero di copertura costo minimo|problema del albero di copertura costo minimo]] sui nodi diversi da $r$, risolvibile ad esempio con [[Algoritmo di Kruskal]] o [[Algoritmo di Prim]]

