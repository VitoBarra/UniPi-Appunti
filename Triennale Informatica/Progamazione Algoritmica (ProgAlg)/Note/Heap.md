---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: "[[Strutture Dati]]"
---
# Struttura dati - Heap
---
l **Heap** è una [[Strutture Dati]] di solito implementata con un [[array]] e serve ad implementare [[Coda di Priorita]].

L'heap è una struttura dati che rappresenta un albero binario completo, ossia un albero in cui tutti i livelli, eccetto forse l'ultimo, sono completamente riempiti, e in cui i nodi sono inseriti da sinistra verso destra. Grazie a questa caratteristica, è particolarmente efficiente la sua rappresentazione tramite [[array]], evitando l'uso esplicito di puntatori per la navigazione tra genitori e figli.

In un heap minimo, la proprietà fondamentale è che ogni nodo ha un valore minore o uguale a quello dei suoi figli. Viceversa, in un heap massimo ogni nodo ha un valore maggiore o uguale a quello dei suoi figli. Questa proprietà consente di accedere rapidamente al minimo o al massimo elemento in tempo $O(1)$, rendendo l'heap ideale per la gestione delle [[Coda di Priorita]].

La rappresentazione tramite [[array]] sfrutta una semplice relazione tra gli indici degli elementi per individuare i parentali e i figli di ciascun nodo:
- Dato un nodo in posizione $i$, il suo genitore si trova in posizione $\left\lfloor \frac{i-1}{2} \right\rfloor$.
- I figli sinistro e destro si trovano rispettivamente in posizione $2i + 1$ e $2i + 2$.

L'inserimento di un elemento richiede l'aggiunta in coda all'array e un successivo processo di risalita ("heapify up" o "bubble up") per ristabilire la proprietà dell'heap. Questo processo ha complessità temporale $O(\log n)$, dove $n$ è il numero di elementi presenti.

La rimozione dell'elemento prioritario (il minimo in un heap minimo o il massimo in un heap massimo) avviene sostituendo la radice con l'ultimo elemento dell'array e applicando un processo di discesa ("heapify down" o "bubble down"), anch'esso con complessità $O(\log n)$.

Grazie a queste operazioni efficienti, l'heap è la base per l'algoritmo di [[Heap Sort]], che permette di ordinare un array in tempo $O(n \log n)$, senza necessità di memoria ausiliaria aggiuntiva, sfruttando la stessa area di memoria dell'array originale.

L'implementazione tramite [[array]] evita sprechi di spazio tipici di altre rappresentazioni ad albero, mantenendo sempre una buona località di riferimento in memoria, fattore che ottimizza le prestazioni su architetture moderne.

L'heap non consente una ricerca arbitraria efficiente, avendo complessità $O(n)$ per tale operazione, ma eccelle nelle operazioni di inserimento e rimozione dell'elemento di massima o minima priorità, rendendolo uno strumento privilegiato per algoritmi come [[Dijkstra]] e [[Prim]].
