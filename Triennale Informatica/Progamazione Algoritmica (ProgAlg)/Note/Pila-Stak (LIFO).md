---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: Strutture Dati
---
# Pila-Stak (LIFO)
---
la **pila o stak** è una [[Strutture Dati|Struttura dati]] caratterizzata da una politica di accesso agli elementi di tipo *Last-In First-Out* (LIFO), dove l’ultimo elemento inserito è il primo a essere rimosso. Ogni operazione di inserimento o rimozione avviene esclusivamente da un'estremità della struttura, denominata *top*.

Le operazioni fondamentali associate a questa struttura sono principalmente due. L'operazione di **push**, che consente l'inserimento di un nuovo elemento sulla cima della pila, e l'operazione di **pop**, che rimuove e restituisce l’elemento attualmente presente in cima. Formalmente:

- **push(x):** inserisce l’elemento $x$ nella pila
- **pop():** restituisce e rimuove l’elemento presente in cima alla pila

A queste si può aggiungere l’operazione **peek** (o **top**), che restituisce l’elemento in cima senza rimuoverlo:

- **peek():** restituisce l’elemento in cima senza modificarne la struttura

Dal punto di vista dell’implementazione, la pila può essere realizzata mediante [[Array]] o [[Lista Collegata|liste collegate]]. Nella rappresentazione tramite array, il *top* corrisponde all’indice dell’ultimo elemento inserito, mentre nella lista collegata, il *top* è il nodo di testa.

L’utilizzo della pila risulta particolarmente utile in numerosi contesti computazionali, come l’implementazione di [[Chiamata Ricorsiva|chiamate ricorsive]], la gestione della memoria tramite lo [[Stack Frame|stack frame]] durante l’esecuzione dei programmi, il controllo di [[Bilanciamento di parentesi|bilanciamento delle parentesi]], nonché negli algoritmi di [[Depth-First Search|ricerca in profondità (DFS)]].

Il comportamento LIFO può essere rappresentato schematicamente come segue:

$$
\begin{array}{|c|}
\hline
\text{top} \\
\hline
x_n \\
\hline
x_{n-1} \\
\hline
\vdots \\
\hline
x_1 \\
\hline
\end{array}
$$

Ogni nuova chiamata a **push(x)** inserisce un elemento sopra $x_n$, mentre **pop()** rimuove $x_n$.

La complessità temporale delle operazioni principali è costante:

- $T_{\text{push}} = O(1)$
- $T_{\text{pop}} = O(1)$
- $T_{\text{peek}} = O(1)$

La gestione efficiente di queste operazioni rende la pila una struttura dati di base ma estremamente potente, alla base di numerosi algoritmi e sistemi.
