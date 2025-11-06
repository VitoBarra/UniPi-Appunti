---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Ricerca A-star 
---
L'algoritmo di **Ricerca $A^*$** è un [[Algoritmi di ricerca informata|Algoritmo di ricerca Informato]] di tipo [[Ricerca Best-first|Best-Frist]] funziona come la [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|ricerca di costo uniforme]] e quindi si la **late goal test** e per assegnare la priorità nella [[Coda di Priorita|coda di priorità]] della **frontiera** si usa la funzione: $$f(n) = g(n)+h(n)$$dove
- $g(n)$ è il costo del cammino dal nodo di partenza al nodo $n$
- $h(n)$ è il la funzione di __valutazione euristica__, è stima della costo del path rimanente tra lo stato $n$ è il goal e vale che  $h(n) \geq 0$  per un qualsiasi nodo non **goal** e $h(goal) = 0$ 

```pseudo
\begin{algorithm}
\caption{A* Search}
\begin{algorithmic}
	\Function{A*-SEARCH}{problem}
	\Return \Call{BEST-FIRST-SEARCH}{problem, g + h}
	\EndFunction
\end{algorithmic}
\end{algorithm}
```




### Comportamento di A*
Il comportamento dell'algoritmo $A^*$ in relazione al costo della soluzione ottimale $C^*$ si può descrivere in termini precisi. 
- **Espande** tutti i nodi raggiungibili dallo stato iniziale lungo un cammino in cui vale $f(n) < C^*$. Questi nodi sono detti ***surely expanded nodes*** 
- Espandere alcuni nodi per cui vale $f(n) = C^*$  (**goal contour**). La selezione di questi nodi dipende dall'ordine con cui vengono esplorati i nodi che li hanno generati
- non espande mai nodi con $f(n) > C^*$. 

algoritmo $A^*$ che utilizza un [[Ricerca informata - Proprieta delle euristiche|euristica consistente]] è ***optimally efficient***, ovvero qualsiasi **altro algoritmo di ricerca** che parte dallo stato **stesso stati iniziale** e impiega **la stessa euristica** deve necessariamente espandere tutti i nodi che $A^*$ espande con $f(n) < C^*$, questo viene dal fatto che ciascuno di questi nodi potrebbe appartenere ad un percorso ottimale e, pertanto, non possono essere esclusi a priori dal processo di espansione.

una delle conseguenze di questa proprietà è fatto che $A^*$  fa **pruning** di alberi di ricerca non necessari, ovvero evita delle strade non fruttuose che altri algoritmi come [[Ricerca in ampiezza (BF)|BF]] e [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|UC]] avrebbero esplorato.


## Analisi della complessità
ai fini di analizzare le prosperità del algoritmo si definisce la **funzione di valutazione ideale** come:
**sia**
- $g^*(n)$ costo del __cammino minimo__ dalla $root$ a $n$
- $h^*(n)$ costo del __cammino minimo__ da $n$ a $goal$ ed è detto **oracolo**
la **funzione di valutazione ideale** $f^*(n)$ che rappresenta il costo del cammino minimo da nodo radice a nodo goal, passando $n$ è definita come:$$C^* = f^*(n)=g^*(n)+h^*(n)$$in casi reali **generali** abbiamo:
- $g(n) \geq g^*(n)$ ovvero il costo che abbiamo trovato per arrivare a nodo $n$ non è quello **ottimale**, perche potremmo averlo raggiunto su un percorso non ottimale
- $h(n)$ che è sempre stima di $h^*(n)$.


**Completezza**: è **completo** se non esistono infiniti nodi per cui vale $f(n) < C^*$  e dove i costi $c_{ij}\geq\epsilon >0$ dove $\epsilon$ è il costo minimo di un arco. è utile definire un costo minimo per evitare che l' algoritmo si incastri in situazioni del tipo![[IMG - discesa per path con costi degli archi sempre minore.jpeg]]
**Ottimale** se spazio degli stati __[[Alberi|albero]]__
**Ottimale** se spazio degli stati **_[[Grafi|grafo]]_** l euristica deve essere **[[Ricerca informata - Proprieta delle euristiche|ammissibile]]** questi si può __dimostrare per contraddizione__, la dimostrazione segue: $$
\begin{array}{rcl}
f(n) & > & C^* \quad \text{(otherwise $n$ would have been expanded)} \\
f(n) & = & g(n) + h(n) \quad \text{(by definition)} \\
f(n) & = & g^*(n) + h(n) \quad \text{(because $n$ is on an optimal path)} \\
f(n) & \leq & g^*(n) + h^*(n) \quad \text{(because of admissibility, $h(n) \leq h^*(n)$)} \\
f(n) & \leq & C^* \quad \text{(by definition, $C^* = g^*(n) + h^*(n)$)}
\end{array}
$$ le ultime due linee si contraddicono e quindi non è possibile che l algoritmo ritorno un percorso **non ottimale**, con questa condizione si può raggiungere attraverso più path lo stesso nodo ma alla fine si espanderà per primo quello con il costo ottimale.
Invece sotto la condizione di **_[[Proprieta delle euristiche per ricerca informata|Consistenza]]_** (detta anche _monotonicità_) leggermente piu forte del __ammisibilità__ si può dimostrare che la prima volta che l'algoritmo incontra un nodo allora quello è già sul cammino ottimo. ciò si può __dimostrare per contraddizione__ come 
$$\begin{array}{rcl}
			
			h(n)  & \leq &  c(n,a,n’) + h(n’)& \text{(consistency)}& \implies \\
			g(n)+h(n)  & \leq &  c(n,a,n’)+g(n) + h(n’) & & \implies\\
			g(n)+h(n)  & \leq &  g(n’)+h(n’) & & \implies \\
			f(n)  & \leq &  f(n’)
			
			\end{array}$$
senza un euristica ammissibile l'__ottimalità__ non è __garantita__, ma il costo risulta ottimo  in due casi 
- se l'eurisitica è [[Ricerca informata - Proprieta delle euristiche|ammissibile]] per almeno un path fino a quel nodo
- se la __sovrastima__ del eristica non supera $h(n) < C^2-C^*$  dove $C^*$ e $C^2$ sono il __costo ottimo reale__ e il __secondo costo ottimo__ 



**[[Complessita|Complessita in tempo]]**: esponensiale nella lunghezza della soluzione e relativa al errore di $h$  
**[[Complessita|Complessita in meoria]]**: tiene tutti i nodi in memoria


>[!note]
>[[Ricerca in ampiezza (BF)|BF]] e [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|UC]] sono ottimali siccome equivale a fare un $A^*$ con $h(n)=0$ che è sempre ammisibile








