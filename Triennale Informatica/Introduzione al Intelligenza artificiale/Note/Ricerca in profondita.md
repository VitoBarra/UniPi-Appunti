---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca in profondità DF
---
è un [[Algoritmi di ricerca|Algoritmo di ricerca]] che utilizza la strategia [[Coda struttura dati|LIFO]] implementando cosi un algoritmo di esplorazione [[Algoritmo di ricerca Depth-Frist]], fa da un taglio su i rami completamente esplorati diminuendo il consumo di memoria
![[Pasted image 20230212011953.png]]



### Analisi della complessità
Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)

##### Versione ad albero
- _Strategia NON completa_ può generare loop
	- i loop sono evitabili  senza l utilizzo di memoria extra controllando i nuovi stati con i stati sul percorso da radice al nodo corrente. questo pero non evita cammini ridondanti e non garantisce la completezza in caso di spazio di stati infiniti
- _Strategia NON ottimale_
	- Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
-  _Complessità nel tempo_ (nodi generati) $O(b^m)$ che potrebbe essere maggiore $O(b^d)$  
- _Complessità spazio_ (nodi in memoria): $O(bm)$ _Cammino dalla radice al nodo_ + _fratelli inesplorati_ 
- ##### Versione a grafo
- _Strategia completa_ in spazi FINITI altrimenti _NON completo_
- _Strategia NON ottimale_
	- Può incontrare  uno stato goal senza aver controllato altri percorsi magari migliori
- _[[Complessita]] nel tempo_ (nodi generati) $O(b^m)$ che potrebbe essere $O(b^d)$ 
- _[[Complessita]] spazio_ (nodi in memoria): $O(b^d)$ _percorso che ha tutti gli stati_ 


### DF ricorsiva
una variante del algoritmo genera solo il percorso che si sta esplorando e genera gli altri facendo _backtraking_ al momento del bisogno
cosi facendo la complessità in spazio diventa $O(m)$

```Python
def recursive_depth_first_search(problem, node): 
#    """Ricerca in profondita' ricorsiva """ 
	# controlla se lo stato del nodo e' uno stato obiettivo 
	if problem.goal_test(node.state): 
		return node.solution() # in caso contrario continua 
	for action in problem.actions(node.state):
		child_node = node.child_node(problem, action)
		result = recursive_depth_first_search(problem, child_node)
		if result is not None:
		return result
	return None
```

nella pratica si genera solo un nodo e si esplora quello evitando di tenere in memoria nodi che si esploreranno in futuro per poi tornarci [[Ricorsione|ricorsivamente]]
