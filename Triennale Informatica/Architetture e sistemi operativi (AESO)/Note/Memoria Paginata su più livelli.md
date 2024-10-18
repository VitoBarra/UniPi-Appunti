---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Memoria Paginata su più livelli
---
La memoria paginata su più livelli è un implementazione della [[Memoria Virtuale]]. è realizzata su più livelli riesce ad implementare le stesse funzioni di una [[Memoria Segmentata paginata]] é fatta in modo da aver ogni livello che entra interamente in un page frame, solo il primo livello deve essere del tutto pieno mentre gli altri vengono allocato solo se un processo sta utilizzando quel particolare indirizzo

![[Untitled 2 5 1.png]]

## Traduzione

gli indici sono formati da n parti e offset dove :

- **n parti**: sono gli indici di livello e ogni parte indica il livello successivo
- **offset**: indica quanto aggiungere page frame trovato la ultimo livello

quindi la [[Traduzione degli indirizzi virtuali|traduzione]] sarà data da: L1\[L2\]…\[LN\]+offset

### Vantaggi

- Stessi di [[Memoria Segmentata paginata]] ma occupa meno spazio non allocando i livelli non necessari
