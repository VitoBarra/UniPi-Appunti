---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: 
SubTopic:
---

# Struttura dati - Coda (FIFO)
---
la **coda** è una [[strutture dati|strutture dati]] caratterizzata dal principio FIFO (*First In, First Out*), in cui il primo elemento inserito è il primo a essere rimosso. Questo comportamento la distingue da altre strutture come lo [[Pila-Stak (LIFO)|stack]], che segue invece il principio LIFO (*Last In, First Out*).

Una coda può essere rappresentata come una sequenza ordinata di elementi, nella quale gli inserimenti avvengono sempre in fondo (operazione detta *enqueue*) e le rimozioni avvengono sempre in testa (operazione detta *dequeue*). Formalmente, indicando la coda come $Q$, si ha:
- inserimento: $Q \gets Q \cup \{x\}$ con $x$ in coda
- rimozione: $x \gets \text{head}(Q)$, seguito da $Q \gets Q \setminus \{x\}$

Le operazioni fondamentali sono:
- **Enqueue($x$)**: inserisce l'elemento $x$ in coda.
- **Dequeue()**: estrae e restituisce l'elemento in testa.
- **IsEmpty()**: verifica se la coda è vuota.

Le implementazioni più comuni prevedono l'uso di array circolari o liste concatenate. Nell'implementazione tramite array circolare, la posizione di testa e coda è mantenuta tramite indici che si aggiornano modularmente:
$$
\text{head} \gets (\text{head} + 1) \bmod N \\
\text{tail} \gets (\text{tail} + 1) \bmod N
$$
dove $N$ è la dimensione massima dell'array.

L'uso di liste concatenate, invece, consente una gestione dinamica della memoria, evitando il problema del riempimento statico dell'array. In tale caso, ogni nodo contiene un dato e un riferimento al successivo.

Le code trovano applicazione in numerosi contesti computazionali, tra cui:
- la gestione dei processi nei sistemi operativi
- la simulazione di sistemi a eventi discreti
- la gestione delle richieste nelle risorse condivise (code di stampa, code di rete)

Dal punto di vista della complessità computazionale, le principali operazioni hanno costo costante $O(1)$ sia per l’inserimento che per la rimozione, a condizione che la struttura dati sottostante sia gestita correttamente.

[[immagine-coda-fifo]] mostra schematicamente il comportamento della struttura, evidenziando l'ordine delle operazioni e il flusso degli elementi attraverso il sistema.

Le varianti più comuni della coda includono la [[strutture dati - coda prioritaria|coda prioritaria]] e la [[strutture dati - coda doppia|deque]], che estendono il comportamento base per soddisfare esigenze computazionali specifiche.
