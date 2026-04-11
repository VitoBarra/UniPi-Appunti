---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Spectral Graph Theory
---
La **Spectral Graph Theory** è un’area della [[Graph Theory|Graph Theory]] che studia la struttura dei **grafi** attraverso lo **spettro delle matrici associate al grafo**, cioè gli [[Autovettori e Autovalori|autovalori e autovettori]] delle [[Matrici|matrici]] che rappresentano il **grafo**. L’idea centrale è che molte **proprietà topologiche** di un grafo possano essere dedotte dalle proprietà spettrali delle sue rappresentazioni matriciali.

Le **matrici** più importanti associate a un grafo $G=(V,E)$ sono:
- **Adjacency matrix** $A$
- **Degree matrix** $D$
- **Graph Laplacian** $L$

###### Adjacency Matrix
Per un grafo con $N$ nodi la **matrice di adiacenza** rappresenta la struttura del grafo ed è una matrice quadrata $A \in \mathbb{R}^{N \times N}$ definita come text $$A_{ij} =
\begin{cases}
w_{ij} & \text{se } (i,j)\in E \\
0 & \text{altrimenti}
\end{cases}$$ text dove $w_{ij}$ rappresenta il **peso** dell’arco nel caso di **grafi pesati**. Nei grafi **non pesati** si ha semplicemente $A_{ij} \in \{0,1\}$, mentre per grafi **non orientati** la matrice è **simmetrica** ($A_{ij}=A_{ji}$).

Le proprietà spettrali della matrice $A$ permettono di studiare caratteristiche globali della rete come **centralità**, **influenza** e **struttura topologica**.

###### Potenze della matrice di adiacenza
Le potenze della matrice di adiacenza contengono informazioni sui **cammini nel grafo**. In particolare l’elemento text $$(A^k)_{ij}$$ text rappresenta il **numero di cammini di lunghezza $k$** tra il nodo $i$ e il nodo $j$.

Per esempio, per $k=2$:
- se $(A^2)_{ij} > 0$, allora i nodi $i$ e $j$ non sono necessariamente collegati direttamente
- tuttavia condividono **almeno un vicino comune**

###### Connettività del grafo
La **connettività** di un grafo può essere espressa attraverso le potenze della matrice di adiacenza. Un grafo è **connesso** se per ogni coppia di nodi $i,j$ esiste almeno un cammino che li collega. In termini matriciali: $$\sum_{k=1}^{N-1} (A^k)_{ij} > 0$$dove $N$ è il numero di nodi del grafo. Se questa somma è nulla per una coppia $(i,j)$, i due nodi appartengono a **componenti connesse differenti**.

###### Degree Matrix
La **degree matrix** $D$ è una [[Matrici quadrate|matrice quadrata diagonale]] che contiene i gradi dei nodi: $$D_{ii} = k_i = \sum_j A_{ij}$$tutti gli altri elementi sono zero. Questa matrice rappresenta la **connettività locale** dei nodi nel grafo e risulta simmetrica per **grafi** non orientati 


###### Graph Laplacian
Il **Laplaciano del grafo** è definito come $$L = D - A$$Questa matrice può essere interpretata come un **operatore di diffusione discreto** sul grafo e ha un ruolo centrale nello studio dinamico delle reti.

Alcune proprietà fondamentali:
- la matrice è **[[Matrici quadrate|simmetrica]]** per grafi non orientati
- tutte le **righe sommano a zero**
- il **numero di [[Autovettori e Autovalori|autovalori]] nulli** corrisponde al numero di **componenti connesse** del grafo

###### Densità
La **densità** di un grafo misura quanto la rete è connessa rispetto al numero massimo di archi possibili.  
Per un grafo non orientato con $N$ nodi e $M$ archi è definita come text $$\rho = \frac{2M}{N(N-1)}$$Quando $$\rho \ll 1$$il grafo è dettto **sparso**, cioè la maggior parte delle possibili connessioni tra nodi non è presente.