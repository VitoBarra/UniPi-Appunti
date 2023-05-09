---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Ricerca Greedy best-frist AI
---
è un [[Algoritmi di ricerca informati per AI|Algoritmo di ricerca informata]] in cui la _funzione di valutazione_ $f$ è uguale alla funzione di _valutazione euristica_
$$f(x)=h(x)$$

## Analisi

Sia 
- $b=$ fattore di ramificazione (*B*ranching) quindi il numero massimo di successori
- $d=$ Profondità del nodo obiettivo più superficiale (*D*epth)
- $m=$ lunghezza massima dei cammini nello spazio degli stati (*M*ax)
##### Versione albero 
- _Strategia NON completa_ può finire in cicli
- _Strategia NON ottimale_
- _[[Complessita]] nel tempo_  $O(b^m)$
	- con una buona euristica pero si può ridurre di molto la complessità ma questa dipende dal problema specifico
- _[[Complessita]] spazio_ (nodi in memoria): $O()$
- ##### Versione grafo
- _Strategia completa_ se spazio degli stati finiti
	- _NON completa_ altrimenti
- _Strategia NON ottimale_
-  _[[Complessita]] nel tempo_  $O(b^m)$ 
- _[[Complessita]] spazio_ (nodi in memoria): $O()$


