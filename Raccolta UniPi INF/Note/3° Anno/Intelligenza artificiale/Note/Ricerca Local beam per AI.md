---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Ricerca Local beam per AI
---
è un algoritmo versione della [[Ricerca Beam per AI|Ricerca beam]] per  [[Ricerca locale|Ricerca locale]]   

## Beam Search

- Si tengono in memoria $k$ stati, anziché uno solo
- ad ogni passo si generano i successori di tutti i $k$ stati
- ad ogni passo si generano i successori di tutti i $k$ stati
	- Se si trova in goal ci si ferma
	- Altrimenti si prosegue con i $k$ migliori tra questi 

### Versione stocastica
- Si introduce un elemento di casualità
- in questa variante si scelgono i $k$ successori, ma con probabilità maggiore per i migliori
