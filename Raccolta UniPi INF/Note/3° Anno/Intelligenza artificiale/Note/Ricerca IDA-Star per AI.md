---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Ricerca IDA* per AI
---
è un [[Algoritmi di ricerca informati per AI|Algoritmo di ricerca informata]]  è basata su [[Ricerca A-Star per AI|A*]] combinando l idea di ricerca iterativa di [[Ricerca con approfondimento iterativo ID-AI|ID]] ma cambia la metrica su cui si decide  quando fermarsi. Si scende quindi il profondità fino a raggiungere un limite impostato su $f$ detto $f-$limit 
ad ogni interazione $f-$limit viene aumentato

__Cruciale__ è la scelta dell'incremento per garantire l’ ottimalità 
- costo azioni _fisse_:
	-  il limite viene incrementato del costo delle azioni. 
-  costo azione _variabili_:
	- si incrementa del costo minimo
	- si fissa il valore di $f-$limit al minimo delle $f$ scartate perché superava il limite


## Analisi

Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)
- $\epsilon=$ minimo costo degli archi 

- _Strategia completa e ottimale_:
	- Se le azioni hanno costo costante $k$  e $f-$limit viene incrementato di $k$ 
	- Se le azioni hanno costo variabile e l'incremento di $f-limit$ è $\geq \epsilon$  
	- Se il nuovo $f-$limit $=min$. valore $f$ dei nodi generati ed esclusi all'iterazione precedente
- _[[Complessita]] nel tempo_  stessa di [[Ricerca con approfondimento iterativo ID-AI|ID]]
- _[[Complessita]] spazio_ (nodi in memoria): $O(bd)$
