---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Ricerca di costo uniforme UC-AI
---
è un [[Algoritmi di ricerca per AI|Algoritmo di ricerca]] che utilizza una [[Struttura dati - Coda di Priorita|Coda di priorita]]  ed è una generalizzazione con i costi di [[Ricerca in ampiezza BF-AI|BF]] ma invece di espandere la frontiera si espande il nodo di costo più basso non ancora esplorato


```python
def uniform_cost_search(problem): #"""Ricerca-grafo UC"""
explored = [] # insieme (implementato come una lista) degli stati gia' visitati 
node = Node(problem.initial_state) # il costo del cammino e' inizializzato nel costruttore del nodo 
frontier = PriorityQueue(f = lambda x:x.path_cost) # la frontiera e' una coda coda con priorita' #lambda serve a definire una funzione anonima a runtime 
frontier.insert(node) 
while not frontier.isempty(): 
# seleziona il nodo 
node = frontier.pop() # estrae il nodo con costo minore, per l'espansione 
if problem.goal_test(node.state):
	return node.solution(explored_set = explored)
else: # se non lo e' inserisci lo stato nell'insieme degli esplorati 
	explored.append(node.state) 
for action in problem.actions(node.state):
	child_node = node.child_node(problem, action) 
	if (child_node.state not in explored) and (not frontier.contains_state(child_node.state)):
	 frontier.insert(child_node) 
	 elif frontier.contains_state(child_node.state) and (frontier.get_node(frontier.index_state(child_node.state)).path_cost > child_node.path_cost):
	 frontier.remove(frontier.index_state(child_node.state)) 
	 frontier.insert(child_node) 
return None # in questo caso ritorna con fallimento
```

## Analisi
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)
- $C^*$ = costo della soluzione ottima
- $\epsilon=$ costo minimo (tutti i costi sono $\geq \epsilon >0$)

- _Strategia completa_ se costo $\epsilon >0$
- _Strategia ottimale_ se costo $\epsilon >0$
- _[[Complessita]] nel tempo_  $O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor})$ 
	- $\left\lfloor C^* /\epsilon\right\rfloor$ numero di mosse ne caso peggiore
	- + 1 per post controllo necessaria per l ottimalità
	- 
>[!warning]
>$O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor})$  può essere molto maggiore di $O(b^d)$ siccome l algoritmo può prendere [[cammini su grafi|cammini]] con costi sempre più piccoli
- _[[Complessita]] in spazio_ $O(b^{1+\left\lfloor C^* /\epsilon\right\rfloor})$ 

> [!note]
> se tutti i costi sono uguali l algoritmo si comporta come [[Ricerca in ampiezza BF-AI|BF]] ma con complessità $O(b^{d+1})$ per  spazio e tempo. questo è dato dal post controllo cosa che fa espandere nodi non necessari