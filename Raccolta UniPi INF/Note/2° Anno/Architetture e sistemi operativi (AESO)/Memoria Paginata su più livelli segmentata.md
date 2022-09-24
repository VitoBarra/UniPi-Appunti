---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Memoria Paginata su più livelli segmentata
---
La memoria paginata su più livelli è un implementazione della [[Memoria Virtuale]].  è identica alla [[Memoria Paginata su più livelli]] ma in caso di livelli pieni può supportare direttamente un [[Memoria Segmentata|segmento]] in moda poter skippare livelli di in direzione 

>[!nota] 
>da rivedere questa parte potrebbe non essere corretta

## Traduzione

identico alla [[Memoria Paginata su più livelli]]

### Vantaggi

- Ottimizzato sulla traduzione siccome se c è un blocco allocato continuo che riempirebbe un intero livello allora il livello precedente punta direttamente a quello saltando quindi un livello
