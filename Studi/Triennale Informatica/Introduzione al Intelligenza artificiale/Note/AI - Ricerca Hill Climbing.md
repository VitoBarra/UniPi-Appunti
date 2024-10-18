---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca Hill Climbing
---
è un algoritmo di [[AI - Ricerca locale|ricerca locale]]  di tipo _[[Algoritmi greedy|greedy]]_ quindi in generale se c è uno stato adiacente che migliora la valutazione si va in quello stato

### Problemi con Hill-Climbing
è molto facile finire in minimi o massimi locali che non necessariamente è la soluzione che stiamo cercando 
![[72BC33B9-FFF8-4A33-925D-0A8A4B38244D.jpeg]]

## varianti migliorative
1. consentire un numero laterale di mosse (plateau)
	1. ovvero anche se il porremo stato ha la stessa valutazione dello saltato attuale va bene si prova a passare in quello stato
2. _Hill-Climbing stocastico_: si sceglie a caso tra le mosse in salita 
	- converge più lentamente ma a volte trova soluzione migliori
3. _Hill-Climbing con prima scelta_: genera mosse a caso finche non ne trova una migliore, in quel caso va in quello stato
	- come la stocastica ma utile quando i successori sono molti, evita la scelta tra tutti (piu efficente)
4. _Hill-Climbing con riavvio casuale_ (random restart): ripete da un punto scelto a caso
	-  se la [[Definizione di Probabilita|Definizione di Probabilita]] di successo $p$ saranno necessarie in media $1\over p$ ripartenza per trovare la soluzione 
	- tendenzialmente _completo_ (daje e daje le provi tutte)
	- se funziona o meno dipende da come è fatta la forma della superfice sui cui stiamo facendo la ricerca
		- funziona male su superfici con molti minimi o massimi locali 
