---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
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

si può definire la **funzione di valutazione ideale** come:
**sia**
- $g^*(n)$ costo del __cammino minimo__ dalla $root$ a $n$
- $h^*(n)$ costo del __cammino minimo__ da $n$ a $goal$ ed è detto **oracolo**
la **funzione di valutazione ideale** $f^*(n)$ che rappresenta il costo del cammino minimo da nodo radice a nodo goal, passando $n$ è definita come:$$f^*(n)=g^*(n)+h^*(n)$$in casi reali abbiamo:
- $g(n) \geq g^*(n)$ ovvero il costo che abbiamo trovato per arrivare a nodo $n$ non è quello **ottimale**.
- $h(n)$ che è sempre stima di $h^*(n)$ 




## Analisi della complessità
**Completezza** se $g(n) \geq d(n) \cdot \epsilon$  dove $\epsilon >0$ costo minimo di un arco, il costo minimo vine usato per evitare che l algoritmo si incastri in situazioni del tipo![[IMG - discesa per path con costi degli archi sempre minore.jpeg]]
questo si può Dimostrazione come segue: 
- Sia $n’$ un nodo nella _frontiera_  che è sul cammino che porta al nodo goal
- $n’$ prima o poi verrà espanso siccome non possono esiste  infiniti nodi con $f(x) \leq f(n’)$
- questo deriva dalla condizione imposta per la completezza
	- Non può esiste un percorso infinito con archi a crescita infinitesimale
- iterando prima o poi si arriva al goal 


**Ottimale** se spazio degli stati __[[Alberi|albero]]__
**Ottimale** se spazio degli stati **_[[Grafi|grafo]]_** l euristica deve essere **[[1- del me|ammissibile]]** questi si può __dimostrare per contraddizione__, assumendo che $C^*$ sia il costo ottimo reale per lo stato $n$ la dimostrazione segue: $$
\begin{array}{rcl}
f(n) & > & C^* \quad \text{(otherwise $n$ would have been expanded)} \\
f(n) & = & g(n) + h(n) \quad \text{(by definition)} \\
f(n) & = & g^*(n) + h(n) \quad \text{(because $n$ is on an optimal path)} \\
f(n) & \leq & g^*(n) + h^*(n) \quad \text{(because of admissibility, $h(n) \leq h^*(n)$)} \\
f(n) & \leq & C^* \quad \text{(by definition, $C^* = g^*(n) + h^*(n)$)}
\end{array}
$$ le ultime due linee si contraddicono e quindi non è possibile che l algoritmo ritorno un percorso **non ottimale**, con questa condizione si può raggiungere attraverso più path lo stesso nodo ma alla fine si espanderà per primo quello con il costo ottimale.
Invece sotto la condizione di **_[[A-Star - Euristiche|Consistenza]]_** (detta anche _monotonicità_) leggermente piu forte del __ammisibilità__ si può dimostrare che la prima volta che l algoritmo incontra un nodo allora quello è già sul cammino ottimo. ciò si può __dimostrare per contraddizione__ come 
$$\begin{array}{rcl}
			
			h(n)  & \leq &  c(n,a,n’) + h(n’)& \text{(consistency)}& \implies \\
			g(n)+h(n)  & \leq &  c(n,a,n’)+g(n) + h(n’) & & \implies\\
			g(n)+h(n)  & \leq &  g(n’)+h(n’) & & \implies \\
			f(n)  & \leq &  f(n’)
			
			\end{array}$$


senza un euristica ammissibile l'__ottimalità__ non è __garantita__, ma il costo risulta ottimo  in due casi 
- se l'eurisitica è [[A-Star - Euristiche|ammissibile]] per almeno un path fino a quel nodo
- se la __sovrastima__ del eristica non supera $h(n) < C^2-C^*$  dove $C^*$ e $C^2$ sono il __costo ottimo reale__ e il __secondo costo ottimo__ 



>[!note]
>[[Ricerca in ampiezza (BF)|BF]] e [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|UC]] sono ottimali siccome equivale a fare un $A^*$ con $h(n)=0$ che è sempre ammisibile


### Vantaggi di A*
- $A*$ espande tutti i nodi con $f(n) <C^*$    
- $A*$ espande  alcuni nodi con $f(n) =C^*$ 
- $A*$ non espande alcun nodo con $f(n) > C^*$ 

Quindi alcuni nodi (e suoi sottoalberi) non verranno considerati per l’ espansione (ma restiamo ottimali):
	_pruning_ (h opportuna, più alta possibile tra le ammissibili, fa tagliare molto )


Commenti : 
- con $f(n) > C^*$ Più $f$ è aderente a stima ottimale, più taglio!  
- Cercheremo quindi una h il più alta possibile tra le ammissibili
-  Se molto bassa molti (sino a tutti i) nodi restano minore di $C*$ 
	- Il espando tutti 
- pruning sottoalberi è il punto focale: non li abbiamo già in memoria e evitiamo di generarli  ( decisivo per i problemi di AI a spazio stati esponenziali )


> [!nota]
>   alcuni algoritmi possono essere considerati come casi speciali di A dove:
>  - [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|UC]] : con $f(n)= g(n)$ e quindi  $h(n) = 0$, diventa [[Ricerca in ampiezza (BF)|BF]] se costi tutti uguali
>  - [[Ricerca Greedy best-frist|Greedy best-frist]]: con $f(n)= h(n)$ e quindi  $g(n) = 0$
>  - [[Ricerca in profondita (DF)|DF]]:

Il comportamento dell'algoritmo A* in relazione al costo della soluzione ottimale $C^*$ si può descrivere in termini precisi. A* espande tutti i nodi raggiungibili dallo stato iniziale lungo un cammino in cui ogni nodo soddisfa la condizione $f(n) < C^*$. Questi nodi sono detti *surely expanded nodes* poiché, essendo su percorsi potenzialmente ottimali, devono necessariamente essere esaminati per garantire la correttezza della soluzione.

Successivamente, A* può espandere alcuni nodi che si trovano esattamente sulla *goal contour*, ovvero quei nodi per cui $f(n) = C^*$. La selezione di questi nodi dipende dall'ordine con cui vengono esplorati; alcuni algoritmi potrebbero individuare il nodo obiettivo ottimale immediatamente, mentre altri potrebbero espandere più nodi prima di raggiungerlo.

È importante notare che A* non espande mai nodi con $f(n) > C^*$. Questa caratteristica lo rende *optimally efficient* quando utilizza una euristica consistente. In tale contesto, qualsiasi algoritmo che estende cammini a partire dallo stato iniziale e impiega la stessa informazione euristica deve necessariamente espandere tutti i nodi che A* espande con $f(n) < C^*$. La ragione di questa obbligatorietà risiede nel fatto che ciascuno di questi nodi potrebbe appartenere ad un percorso ottimale e, pertanto, non possono essere esclusi a priori dal processo di espansione.

Per quanto concerne i nodi con $f(n) = C^*$, la loro espansione dipende dalla fortuna dell'algoritmo nel selezionare il nodo ottimale; questa variabilità non incide sulla definizione formale di *optimal efficiency*.




