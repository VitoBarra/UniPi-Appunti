---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
tags:
  - AESO
topic: nota
---

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

