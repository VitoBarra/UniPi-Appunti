---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---
# Ricerca Local beam per AI
---
è un algoritmo versione della [[AI - Ricerca Beam|Ricerca beam]] per  [[AI - Ricerca locale|ricerca locale]]   

## Beam Search

- Si tengono in memoria $k$ stati, anziché uno solo
- ad ogni passo si generano i successori di tutti i $k$ stati
- ad ogni passo si generano i successori di tutti i $k$ stati
	- Se si trova in goal ci si ferma
	- Altrimenti si prosegue con i $k$ migliori tra questi 

### Versione stocastica
- Si introduce un elemento di casualità
- in questa variante si scelgono i $k$ successori, ma con probabilità maggiore per i migliori
