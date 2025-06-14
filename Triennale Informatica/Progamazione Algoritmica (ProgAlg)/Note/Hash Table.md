---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: Strutture Dati
---
# Hash Table
---
Una **hash table** è una [[Strutture Dati|struttura dati]] che implementa un array associativo, ovvero una struttura in grado di mappare chiavi a valori. Il suo funzionamento si basa sull'utilizzo di una funzione di hash, che calcola un indice a partire da una chiave, permettendo un accesso efficiente ai dati. Questo meccanismo rende le operazioni di inserimento, cancellazione e ricerca mediamente molto veloci, con una complessità temporale spesso vicina a $O(1)$ nel caso ideale.

La funzione di hash è un componente fondamentale: prende in input una chiave e restituisce un valore intero, detto hash code, che corrisponde a un indice nell'array sottostante. Idealmente, la funzione dovrebbe distribuire uniformemente le chiavi per evitare collisioni, ovvero situazioni in cui chiavi diverse producono lo stesso hash code. Tuttavia, le collisioni sono inevitabili in pratica e possono essere gestite con diverse strategie, come il concatenamento (dove ogni slot dell'array contiene una lista collegata di elementi) o l'indirizzamento aperto (dove gli elementi vengono spostati in altri slot liberi).

Nel caso del concatenamento, se due chiavi $k_1$ e $k_2$ hanno lo stesso hash code $h$, vengono entrambe memorizzate nello stesso slot come una lista. La ricerca richiede quindi di scorrere la lista, con una complessità che dipende dal numero di elementi in essa contenuti. Per l'indirizzamento aperto, invece, se uno slot è occupato, la funzione di hash viene modificata per trovare uno slot libero, ad esempio utilizzando il linear probing ($h(k, i) = (h'(k) + i) \mod m$), dove $i$ è il tentativo corrente e $m$ la dimensione della tabella.

Le prestazioni di una hash table dipendono fortemente dal fattore di carico $\alpha = \frac{n}{m}$, dove $n$ è il numero di elementi e $m$ la dimensione della tabella. Un $\alpha$ troppo alto aumenta la probabilità di collisioni, mentre un $\alpha$ troppo basso spreca memoria. Spesso viene utilizzato il ridimensionamento dinamico per mantenere $\alpha$ entro un intervallo ottimale.

Le hash table sono ampiamente utilizzate in contesti dove è richiesto un accesso rapido ai dati, come nei database, nelle cache o nell'implementazione di dizionari e set. La loro efficienza le rende preferibili ad altre strutture dati come gli alberi bilanciati in molte applicazioni pratiche, sebbene queste ultime offrano garanzie peggiori nel caso peggiore.