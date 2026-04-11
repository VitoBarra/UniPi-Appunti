---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic: nota
---

# Algoritmi di Ford-Fulkerson
---
L'[[Algoritmi di Ford-Fulkerson|algoritmo di Ford-Fulkerson]] risolve il [[Problema del flusso massimo|problema del flusso massimo]] aumentando iterativamente un [[Flusso su grafo|flusso]] ammissibile lungo un [[Cammino aumentante|cammino aumentante]] del [[Grafo residuo|grafo residuo]].

## Teorema

Se le capacità degli archi di un [[Graph Theory|grafo]] sono intere, allora l'[[Algoritmi di Ford-Fulkerson|algoritmo di Ford-Fulkerson]] trova un [[Flusso su grafo|flusso]] di valore massimo dopo un numero finito di iterazioni.

All'ultima iterazione un [[Taglio su grafo|taglio]] di capacità minima $(N_s,N_t)$ si può calcolare ponendo:

$$
\begin{array}{l}
N_s=\{i\in N\mid \text{esiste in } G(x) \text{ un cammino orientato da } s \text{ a } i\} \\
N_t=\{i\in N\mid \text{non esiste in } G(x) \text{ un cammino orientato da } s \text{ a } i\}
\end{array}
$$
Un altro [[Taglio su grafo|taglio]] di capacità minima $(N'_s,N'_t)$ si può ottenere ponendo:$$
\begin{array}{l}
N'_s=\{i\in N\mid \text{non esiste in } G(x) \text{ un cammino orientato da } i \text{ a } t\} \\
N'_t=\{i\in N\mid \text{esiste in } G(x) \text{ un cammino orientato da } i \text{ a } t\}
\end{array}
$$Il [[Taglio su grafo|taglio]] di capacità minima è unico se e solo se i due tagli precedenti coincidono.

###### Dimostrazione
La dimostrazione segue dalla [[Condizione di Ottimalità Max flow - Min cut|Condizione di Ottimalità Max flow-Min cut]].

## Algoritmo

1. Poni $x=0$ su tutti gli archi.
2. Costruisci il [[Grafo residuo|grafo residuo]] $G(x)$.
3. Se esiste un [[Cammino aumentante|cammino aumentante]] $C$ in $G(x)$, calcola
$$
\delta=\min\{r_{ij}:(i,j)\in C\}
$$
e aggiorna il flusso spedendo $\delta$ unità lungo $C$.
4. Aggiorna il [[Grafo residuo|grafo residuo]] e ripeti il passo precedente.
5. Se non esiste alcun [[Cammino aumentante|cammino aumentante]], il flusso corrente è massimo.

L'aggiornamento del flusso lungo $C$ si effettua nel modo seguente:
- se $(i,j)$ è un arco percorso in avanti, si pone $x_{ij}=x_{ij}+\delta$
- se $(j,i)$ è un arco percorso all'indietro, si pone $x_{ij}=x_{ij}-\delta$

## Interpretazione

A ogni iterazione l'[[Algoritmi di Ford-Fulkerson|algoritmo di Ford-Fulkerson]] cerca un [[Cammino aumentante|cammino aumentante]] rispetto al flusso corrente. Se tale cammino esiste, il flusso viene aumentato della massima quantità possibile compatibile con le capacità residue degli archi del cammino. Se tale cammino non esiste, il flusso corrente è ottimo e dal [[Grafo residuo|grafo residuo]] si può ricavare anche un [[Taglio su grafo|taglio]] di capacità minima.

## Problematiche

Se non viene fissata una regola precisa per la scelta del [[Cammino aumentante|cammino aumentante]], la convergenza dell'algoritmo può essere molto lenta.

Si consideri, ad esempio, un problema di flusso massimo da $1$ a $4$ in cui gli archi $(1,2)$, $(1,3)$, $(2,4)$ e $(3,4)$ hanno capacità $1000$, mentre l'arco $(2,3)$ ha capacità $1$. Se si scelgono come cammini aumentanti percorsi del tipo $1$-$2$-$3$-$4$, $1$-$3$-$2$-$4$, $1$-$2$-$3$-$4$, e così via, a ogni iterazione si invia soltanto $1$ unità di flusso e l'algoritmo termina dopo $2000$ iterazioni.


## Variante di Edmonds-Karp

La variante di [[Algoritmi di Ford-Fulkerson|Edmonds-Karp]] impone di scegliere a ogni iterazione un [[Cammino aumentante|cammino aumentante]] con il minimo numero di archi. In questo modo l'algoritmo ha complessità polinomiale $O(nm^2)$, dove $n=|N|$ e $m=|A|$.

Per trovare un [[Cammino aumentante|cammino aumentante]] con il minimo numero di archi basta eseguire una visita in ampiezza del [[Grafo residuo|grafo residuo]]. Si mantiene un vettore dei predecessori $p$ e una coda $Q$.

1. Inizializza $p_i=-1$ per ogni $i\neq s$, poni $p_s=0$ e $Q=\{s\}$.
2. Se $Q=\emptyset$, allora STOP: non esistono [[Cammino aumentante|cammini aumentanti]] e $p$ identifica un [[Taglio su grafo|taglio]] di capacità minima con $N_s=\{i\in N:p_i\neq -1\}$ e $N_t=\{i\in N:p_i=-1\}$.
3. Estrai dalla testa della coda un nodo $i$.
4. Se $(i,t)$ appartiene al [[Grafo residuo|grafo residuo]], poni $p_t=i$ e STOP: il vettore $p$ identifica un [[Cammino aumentante|cammino aumentante]].
5. Analizza gli archi uscenti da $i$ nel [[Grafo residuo|grafo residuo]]; per ogni arco $(i,j)$, se $p_j=-1$, poni $p_j=i$ e inserisci $j$ in coda.
6. Ripeti dal passo 2.

