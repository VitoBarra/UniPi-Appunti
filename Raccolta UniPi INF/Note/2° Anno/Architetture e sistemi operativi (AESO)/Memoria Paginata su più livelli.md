# Memoria Paginata su più livelli

memoria implementata su può livelli riesce ad implementare le stesse funzioni di una [[Memoria Segmentata paginata]] é di solito realizzata per aver ogni livello che entra interamente in un page frame, solo il primo livello deve essere del tutto pieno mentre gli altri vengono allocato solo se un processo sta utilizzando quel particolare indirizzo

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 2 5.png]]

## Traduzione

gli indici sono formati da n parti e offset dove :

- **n parti**: sono gli indici di livello e ogni parte indica il livello successivo
- **offset**: indica quanto aggiungere page frame trovato la ultimo livello

quindi l accesso sarà L1[L2]…[LN]+offset

### Vantaggi

- Stessi di [[Memoria Segmentata paginata]] ma occupa meno spazio non allocando i livelli non necessari

### Problematiche

-
