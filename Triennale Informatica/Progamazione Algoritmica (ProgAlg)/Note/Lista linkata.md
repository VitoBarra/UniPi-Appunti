---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: "[[Strutture Dati]]"
---
# Struttura dati - Lista linkata
---
La **lista linkata** è una [[Strutture Dati|Strutture Dati]] utilizzata per rappresentare una sequenza di elementi in modo dinamico. È composta da nodi, dove ciascun nodo contiene un valore (detto **dato** o **valore**) e un puntatore al nodo successivo nella sequenza.

Ogni nodo della lista può essere rappresentato come una struttura contenente due campi principali:
- **valore**: il dato che il nodo rappresenta.
- **puntatore**: un riferimento al nodo successivo.

Formalmente, un nodo $n$ può essere descritto come:
$$
n = (v, p)
$$
dove $v$ è il valore contenuto e $p$ è il puntatore al prossimo nodo.

La lista linkata possiede un puntatore iniziale, comunemente detto **testa** (*head*), che consente l'accesso al primo nodo. Se la lista è vuota, la testa punta a un valore nullo, indicato solitamente come $null$.

L’accesso agli elementi avviene in modo sequenziale: per accedere all’elemento $i$-esimo è necessario percorrere la lista partendo dalla testa e seguendo i puntatori per $i$ passaggi. Tale modalità implica un tempo di accesso medio pari a $O(n)$, dove $n$ rappresenta il numero totale di elementi presenti.

L’inserimento di un nuovo nodo può avvenire in vari punti della sequenza. L'inserimento in testa ha complessità $O(1)$, poiché basta aggiornare il puntatore della testa affinché punti al nuovo nodo. L'inserimento in posizione generica richiede invece un attraversamento della lista fino al nodo precedente, comportando una complessità $O(n)$.

La rimozione di un elemento segue un meccanismo analogo all'inserimento. Rimuovere il primo nodo è un'operazione di complessità $O(1)$, mentre la cancellazione di un nodo in posizione arbitraria comporta una scansione preliminare della lista, richiedendo tempo $O(n)$.

Una variante della lista linkata è la **lista doppiamente linkata**, nella quale ogni nodo contiene un ulteriore puntatore al nodo precedente. In tal caso, ogni nodo è rappresentato come:
$$
n = (v, p_{next}, p_{prev})
$$
dove $p_{next}$ è il puntatore al nodo successivo e $p_{prev}$ quello al nodo precedente. Questa struttura consente una navigazione bidirezionale e semplifica alcune operazioni di inserimento e cancellazione a scapito di un maggior consumo di memoria.

Un'ulteriore estensione è la **lista circolare**, in cui l'ultimo nodo punta nuovamente al primo, formando un ciclo continuo. Tale caratteristica è particolarmente utile in contesti applicativi che richiedono una gestione ciclica delle risorse.

La gestione della memoria nelle liste linkate è dinamica: i nodi vengono allocati e deallocati durante l'esecuzione, permettendo di utilizzare efficientemente lo spazio disponibile senza necessità di preallocazione. Tuttavia, l'uso dei puntatori comporta un sovraccarico in termini di spazio e complessità nella gestione.

Rispetto ad altre [[Strutture Dati|Strutture Dati]], come gli [[Array|Array]], le liste linkate offrono maggiore flessibilità nell'inserimento e cancellazione degli elementi, a fronte di un accesso sequenziale meno efficiente.

