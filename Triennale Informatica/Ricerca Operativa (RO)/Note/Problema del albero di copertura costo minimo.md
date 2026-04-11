---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags: RO
---

# Problema del albero di copertura costo minimo
---
Dato un [[Graph Theory|grafo]] non orientato $G=(N,A)$, in cui ad ogni arco $\{i,j\} \in A$ è associato un costo $c_{ij}$, il problema consiste nel trovare un [[Albero di copertura|albero di copertura]] di costo minimo.

Se $T \subseteq A$ è un [[Albero di copertura|albero di copertura]], il suo costo è:$$\sum_{\{i,j\}\in T} c_{ij}$$L'obiettivo è quindi selezionare un insieme di archi che:
- colleghi tutti i nodi del grafo
- non contenga cicli
- abbia costo totale minimo
Senza perdita di generalità, si può supporre che il grafo sia completo, eventualmente aggiungendo archi di costo molto grande $M$.

## Formulazione come PL 1

Variabili decisionali:
Per ogni coppia di nodi $i,j \in N$ con $i<j$, definiamo:$$
x_{ij}=
\begin{cases}
1 & \text{se l'albero contiene l'arco } (i,j) \\
0 & \text{altrimenti}
\end{cases}
$$La [[Programmazione lineare|formulazione di programmazione lineare]] del problema è:$$
\begin{cases}
\min \sum\limits_{i \in N} \sum\limits_{\substack{j\in N \\ j>i}} c_{ij}x_{ij} \\
\sum\limits_{i \in N} \sum\limits_{\substack{j\in N \\ j>i}} x_{ij} = n-1 \\
\sum\limits_{i \in S} \sum\limits_{\substack{j\in S \\ j>i}} x_{ij} \leq |S|-1 \qquad \forall S \subset N : |S| \geq 3 \\
x_{ij} \in \{0,1\} \qquad i,j \in N \text{ con } i<j
\end{cases}
$$Osservazioni:
- il vincolo $\sum x_{ij}=n-1$ impone che la soluzione selezioni esattamente $n-1$ archi
- i vincoli sui sottoinsiemi $S$ vietano che gli archi scelti formino cicli all'interno di un sottoinsieme proprio di nodi
- questa formulazione mette quindi in evidenza soprattutto l'aspetto di **eliminazione dei cicli**
- per questo motivo richiama più da vicino la logica di [[Algoritmo di Kruskal]], che costruisce l'albero aggiungendo archi di costo minimo ma scartando quelli che chiuderebbero un ciclo

## Formulazione come PL 2

Variabili decisionali:
Per ogni coppia di nodi $i,j \in N$ con $i<j$, definiamo ancora:$$
x_{ij}=
\begin{cases}
1 & \text{se l'albero contiene l'arco } (i,j) \\
0 & \text{altrimenti}
\end{cases}
$$La seconda [[Programmazione lineare|formulazione di programmazione lineare]] del problema è:

$$
\begin{cases}
\min \sum\limits_{i \in N} \sum\limits_{\substack{j\in N \\ j>i}} c_{ij}x_{ij} \\
\sum\limits_{i \in N} \sum\limits_{\substack{j\in N \\ j>i}} x_{ij} = n-1 \\
\sum\limits_{i \in S} \sum\limits_{\substack{j \not\in S \\ j>i}} x_{ij} +
\sum\limits_{i \not\in S} \sum\limits_{\substack{j \in S \\ j>i}} x_{ij} \geq 1 \qquad \forall S \subset N : |S| \geq 1 \\
x_{ij} \in \{0,1\} \qquad i,j \in N \text{ con } i<j
\end{cases}
$$

Osservazioni:
- il vincolo $\sum x_{ij}=n-1$ impone ancora che vengano scelti esattamente $n-1$ archi
- i vincoli di connessione impongono che ogni sottoinsieme proprio di nodi sia collegato al complemento, e quindi che il grafo selezionato sia connesso
- questa formulazione mette quindi in evidenza soprattutto l'aspetto di **connessione** del problema
- per questo motivo richiama più da vicino la logica di [[Algoritmo di Prim]], che fa crescere progressivamente un insieme connesso di nodi scegliendo ogni volta un arco che attraversa un [[Taglio su grafo|taglio]]