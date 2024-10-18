---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Macchine a stati finiti
---


Le macchine a stati finiti costituiscono un metodo sistematico di progettazione delle reti sequenziali sincrone e sono caratterizzata dalla possibilità di salvare $2^k$ stati con $k$ registri che ricevono lo stesso segnali di clock.

una [[Macchine a stati finiti|macchia a stati finiti (FSM)]] è composta da un [[Registro]] che immagazzina lo stato e due blocchi di [[Reti Combinatorie|logica combinatoria]], logica di stato prossimo e logica d’uscita,

possono essere di due tipo:

### Machina di  Moore

macchine alla Moore, le uscite dipendono esclusivamente dallo stato presente della macchina

![[Untitled 21 1.png]]

### Machina di Mealy

macchine alla Mealy le uscite dipendono sia dallo stato presente della macchina sia
dagli ingressi attuali.

![[Untitled 1 8 1.png]]

## Codifica

i $k$ stati delle macchine a stati possono essere codificati con $log_2k$ bit di stato oppure utilizando 1 solo bit per strato.

| log | 1 bit |
| --- | --- |
| 01 | 001 |
| 10 | 010 |
| 11 | 100 |

utilizzare il sistema a 1 bit potrebbe rendere la macchina più semplice e quindi richiedere meno hardware ma questo dipende dalla specifica FSM che si vuole realizzare
