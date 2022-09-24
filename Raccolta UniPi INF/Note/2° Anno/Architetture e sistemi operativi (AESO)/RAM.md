---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# RAM
---
la Random Access Memory è una memoria di tipo volatile, ovvero che i dati scritti non persistono con la rimozione del alimentazione

## DRAM

la RAM dinamica è realizata con condenzatore che immagazina il valore 1 se carino o il valore 0 se scarico. lecariche su un condenzatore degradano nel tempo quindi le RAM dinamiche vanno rinfrescate periodicamente riscrivendo il valore contenuto.

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Z-Media/Untitled 19.png]]

### SRAM

le RAM statiche sono realizate con due negatori collegati ad anello che essendo una struttura bistabile non ha bisogno di essere infrescata

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Z-Media/Untitled 1 10.png]]

### Area e ritardo

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Z-Media/Untitled 2 6.png]]

un flip-Flop prende più Area di silicio rispetto ad una  SRAM che ne prende a sua volta di piu rispoetto ad uan DRAM. di conseguenza queste richidono anche piu energia per funzionare.

il tradeoff di questa spesa extra è una velocita superiore.

### SDRAM e DDR SDRAM

Inoltre una DRAM ha un throughput (quantità di bit scambiabili per unità di tempo) nettamente inferiore a quella di una SRAM, perché
deve rinfrescare periodicamente i dati, oltre che dopo ogni lettura. Sono state
sviluppate varie tecnologie DRAM, come le DRAM sincrone (SDRAM, Synchronous DRAM) e le SDRAM a doppia velocità (DDR SDRAM, Double
Data Rate SDRAM) proprio per sopperire a questo problemaLe DDR
SDRAM, dette anche semplicemente DDR, utilizzano sia i fronti di salita sia
quelli di discesa del clock per accedere ai dati e in questo modo duplicano il
throughput a pari frequenza di clock

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
