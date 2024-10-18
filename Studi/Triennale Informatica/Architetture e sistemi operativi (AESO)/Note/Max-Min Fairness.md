---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Max-Min Fairness
---


è una politica in cui si scegliere il task prendendo quello che ha meno tempo accumulato sul processore e la permanenza sul processore dura un time slice.

se un processo fa prerilascio volontario prima della fine del tempo allora redistribuisce il tempo avanzato a tutti i processi ancora in esecuzione massimizzando cosi il minimo di tempo dato ad i processi.

## Caratteristiche



### Pro

- ottimo per Fairness
- evita starvation

### Contro

- alto overhead

## Workload

### Caso Ottimo

- funziona bene in casi di task misti Compute-Bound e I/O-bound

### Caso pessimo

- NESSUNO
