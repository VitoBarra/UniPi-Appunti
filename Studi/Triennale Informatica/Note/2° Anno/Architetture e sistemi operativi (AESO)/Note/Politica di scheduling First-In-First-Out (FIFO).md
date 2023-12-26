---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO FileNotFound
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# First-In-First-Out (FIFO)
---
è l algoritmo di [[Scheduler|scheduling]] più semplice dove i task vengono schedulati con una coda.

## Caratteristiche



### Pro

- *ottimo* per fairness
- evita la starvation

### Contro

- efficacia variabile con workload diversi

## Workload

### Caso Ottimo

- il workload è composto da task tutti di lunghezza simile. minimizza il tempo di risposta medio e massimizza il throughput

### Caso pessimo

- il workload è composto da molti task corti e pochi molto lungi. è il peggiore per il tempo di risposta medio

    [[First-In-First-Out (FIFO]]%20225eae1f95774e86b44941e2c34d6767/Untitled.png)
