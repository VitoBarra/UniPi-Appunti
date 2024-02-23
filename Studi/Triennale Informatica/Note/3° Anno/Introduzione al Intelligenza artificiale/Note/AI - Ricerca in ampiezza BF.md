---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca in ampiezza BF
---
è un [[AI - Algoritmi di ricerca|Algoritmo di ricerca]]  che utilizza la strategia [[Struttura dati - Pila|FIFO]] implementando cosi un algoritmo di esplorazione [[Algoritmo di ricerca Breadth-Frist]] con la differenza di fare un controllo del raggiungimento del nodo goal al momento della generazione dei nodi, questi riduce la complessità

con la BF su alberi si fa un esplorazione per livelli
![[Pasted image 20230212003152.png]]


```Python
def breadth_first_search(problem): # """Ricerca-grafo in ampiezza""" explored = [] # insieme degli stati già visitati (implementato come una lista)
node = Node(problem.initial_state) # il costo del cammino è inizializzato nel costruttore del nodo 
if problem.goal_test(node.state):
	return node.solution(explored_set = explored) 
frontier = FIFOQueue() # la frontiera e' una coda FIFO
frontier.insert(node)
while not frontier.isempty(): # seleziona il nodo per l'espansione
node = frontier.pop()
explored.append(node.state) # inserisce il nodo nell'insieme dei nodi esplorati 
for action in problem.actions(node.state): 
	child_node = node.child_node(problem,action) 
	if (child_node.state not in explored) and (notfrontier.contains_state(child_node.state)): 
	if problem.goal_test(child_node.state): 
		return child_node.solution(explored_set = explored) # se lo stato non e' uno stato obiettivo allora inserisci il nodo nella frontiera 
		frontier.insert(child_node) 
return None # in questo caso ritorna con fallimento
```


### Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)

- _Strategia completa_
	-  non vengono lasciate strade non esplorate siccome si procede per livelli si vede che il nodo goal è almeno sullo stesso livello di quello che si sta esplorando
- _Strategia ottimale_ se gli operatori hanno tutti lo _stesso costo_ $k$, cioè $g(n) = k · depth(n)$, dove $g(n)$ è il costo del cammino per arrivare a $n$ 
-  _[[Complessita]] nel tempo_ (nodi generati) $T(b, d) = 1+ b + b^2 + \dots + b^d\rightarrow O(b^d)$  
 >[!nota]
> Riflettere che il numero nodi cresce exp., non assumiamo di conoscere già il grafo ne una notazione di linearità nel numero nodi . Questo è tipico dei problemi in AI (pensate a quelli generati per le configurazioni dei giochi, con rappresentazione implicita dello spazio stati, non esplicitamente/staticamente in spazi enormi). 
- _[[Complessita]] spazio_ (nodi in memoria): $O(b^d )$ _frontiera_ e $O(b^{d-1})$ per _esplorati_

>[!warning]
>Se il test goal fosse stato fatto al espansione e non alla generazione la complessita in spazio per la frontiera e in tempo sarebbe stata $O(b^{d+1})$

![[Pasted image 20230212011517.png]]
Il problema in questo caso è lo spazio che cresce troppo in fretta