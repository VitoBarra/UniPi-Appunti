---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic:
---
# Ricerca in profondita BackTracking (BDF)
---
la **Ricerca in profondità** o **BackTracking depth-first** (**BDF**) è un [[Algoritmi di ricerca|Algoritmo di ricerca]] variante della [[Ricerca in profondita (DF)| ricerca in profondita]] che oltre a **non** salvare i nodi raggiunti  **NON** salva la **frontiera**, ma utilizza la [[Ricorsione|ricorsione]] per risalire i nodi una volta l algoritmo non trova piu un successore e generare il prossimo stato da esplorare.  



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



##  Analisi della complessità
 [[Complessita|complessità in spazio]] in spazio diventa  $O(m)$
