---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Memoria Segmentata paginata
---
la memoria segmentata pagina è un implementazione della [[Memoria Virtuale]]Ci sono dei segmenti come nella [[Memoria Segmentata]]  ma al posto del segmento continuo nella tabella si ritrova un puntatore ad un array di frame e il paramento Bound diventa size indicando quindi la quantità di frame presenti in quel segmento

![[Untitled 40.png]]

## Traduzione

la traduzione degli indirizzi è composta da 3 pareti:

- **Segment**: indica il segmento da cui prendere la tabella di pagine
- **Page#**: indica in numero di pagina da prendere nella Tabella delle pagine
- **offset**: quanto da aggiungere alla inizio della pagina per raggiungere il dato voluto

quindi la [[Traduzione degli indirizzi virtuali|traduzione]] sarà data da: SegmentTable\[segment\].PageTable\[Page#\]+offset

### Vantaggi

- Stesso per [[Memoria Paginata]]
- **supporto protezione memoria**: la protezione di memoria si ottiene con un bit di permessi sulla singola pagina o sul intero segmento dando cosi la possibilità di funzionare sia corse-grande che fine-grande

### Problematiche
- occupa in memoria tutto lo spazio indirizzabile dal indirizzo virtuale che è solitamente molto alto
