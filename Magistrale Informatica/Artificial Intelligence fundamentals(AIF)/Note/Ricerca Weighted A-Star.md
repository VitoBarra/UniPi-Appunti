---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - "#plus"
Area: 
topic: 
SubTopic:
---

# Ricerca Weighted A-Star
---
Il metodo di ricerca A* presenta molte qualità positive, ma una delle sue principali limitazioni è l’elevato numero di nodi che espande per garantire l’ottimalità della soluzione. Tuttavia, in molti contesti pratici, può essere accettabile rinunciare alla garanzia di ottimalità in cambio di un risparmio significativo in termini di tempo e spazio computazionale, arrivando così a soluzioni **satisficing**, ossia sufficientemente buone.

Quando si utilizza A* con un’euristica **[[Ricerca informata - Proprieta delle euristiche|inamissibile]]**  si corre il rischio di non trovare la soluzione ottima, ma si può ridurre considerevolmente lo spazio di ricerca. In alcune applicazioni, questa approssimazione controllata permette di trovare soluzioni valide in tempi molto più rapidi.

Questo principio è generalizzabile a molti problemi di ricerca tramite l'approccio noto come **Weighted A* search**, nel quale il valore dell’euristica viene ponderato maggiormente. La funzione di valutazione adottata da Weighted A* è definita come:

$$
f(n) = g(n) + W \times h(n)
$$

dove:
- $g(n)$ rappresenta il costo accumulato per raggiungere il nodo $n$,
- $h(n)$ è la stima euristica del costo residuo per arrivare al nodo obiettivo,
- $W$ è un peso
L’aumento del peso $W$ focalizza la ricerca maggiormente verso l’obiettivo, riducendo il numero di stati esplorati. Questo si traduce in una minore espansione dello spazio di ricerca, ma con la possibilità di non identificare il percorso ottimo, specialmente se esso si trova al di fuori del "contorno" di stati raggiunti dal Weighted A*.

Considerando il costo ottimale $C^*$, la soluzione trovata dal Weighted A* avrà un costo compreso tra $C^*$ e $W \times C^*$. In pratica, tuttavia, i costi ottenuti sono frequentemente molto più vicini a $C^*$ che a $W \times C^*$. 

Il Weighted A* può essere interpretato come una generalizzazione di vari algoritmi di ricerca:
- [[Ricerca di costo uniforme o Dijkstra algorithm (UC)]]: $f(n) = g(n)$ con $W = 0$
- [[Ricerca A-Star]]: $f(n) = g(n) + h(n)$ con $W = 1$
- [[Ricerca Greedy best-frist]]: $f(n) = h(n)$ con $W = \infty$
- Weighted A*: $f(n) = g(n) + W \times h(n)$ con $1 < W < \infty$

In questa prospettiva, il Weighted A* può essere descritto come una forma di ricerca **parzialmente greedy**: come la [[Ricerca Greedy best-frist]], dirige la ricerca verso l’obiettivo, ma, a differenza di essa, non ignora completamente il costo accumulato $g(n)$ e può sospendere un percorso qualora stia progredendo lentamente con costi elevati.

Questa trattazione si inserisce nel contesto degli [[Algoritmi di ricerca informata]], in particolare nella famiglia delle [[Ricerca Best-first]], in cui il bilanciamento tra $g(n)$ e $h(n)$ è centrale per determinare il comportamento dell'algoritmo.
