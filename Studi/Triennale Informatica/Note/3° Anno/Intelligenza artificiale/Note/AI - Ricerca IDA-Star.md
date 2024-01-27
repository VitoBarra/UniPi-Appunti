---
type: nota
course: Intelligenza Artificiale
topic: 
tags:
  - IA
Parent MOC: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
---

# Ricerca IDA* 
---
è un [[AI - Algoritmi di ricerca informati|Algoritmo di ricerca informata]]  è basata su [[AI - Ricerca A-Star|A*]] combinando l idea di ricerca iterativa di [[AI - Ricerca con approfondimento iterativo ID|ID]] ma cambia la metrica su cui si decide  quando fermarsi. Si scende quindi il profondità fino a raggiungere un limite impostato su $f$ detto $f_{limot}$ 
ad ogni interazione $f_{limit}$ viene aumentato

__Cruciale__ è la scelta dell'incremento per garantire l’ ottimalità 
- costo azioni _fisse_:
	-  il limite viene incrementato del costo delle azioni. 
-  costo azione _variabili_:
	- si incrementa del costo minimo
	- si fissa il valore di $f_{limit}$ al minimo delle $f$ scartate perché superava il limite


## Analisi
Sia 
- $b$ = fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d$ = Profondità del nodo obiettivo più superficiale (*D*epth)
- $m$= lunghezza massima dei cammini nello spazio degli stati (*M*ax)
- $\varepsilon$ = minimo costo degli archi 

- _Strategia completa e ottimale_:
	- Se le azioni hanno costo costante $k$  e $f_{limit}$ viene incrementato di $k$ 
	- Se le azioni hanno costo variabile e l'incremento di $f_{limit} \geq \varepsilon$  
	- Se il nuovo $f_{limit} = min$. valore $f$ dei nodi generati ed esclusi all'iterazione precedente
- _[[Complessita]] nel tempo_ stessa di [[AI - Ricerca con approfondimento iterativo ID|ID]]
- _[[Complessita]] spazio_ (nodi in memoria): $O(bd)$
