---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Politica di Scheduling Shortest Job First (SJF)
---


è una politica di [[Scheduler|Scheduling]] in cui si scegliere il task con il tempo rimanente più breve è puramente teorico siccome per implementarlo servirebbe conoscere la lunghezza dei task ovvero il futuro. per quanto sia teorico questo si può approssimare

## Caratteristiche



### Pro
- *ottimo* per il tempo di risposta medio

### Contro
- peggiore in per la Varianza
- Non sempre evita la starvation
- non garantisce la fairness

## Workload

### Caso Ottimo

- sempre ottimo per tempo di risposta medio per ogni workload il migliore anche per altri paramenti se è composto da task di lunghezza simile

### Caso pessimo

- nel workload vengono aggiunti spesso task molto piccoli non dando la possibilità a task lunghi di essere eseguiti questi possono andare in starvation


>[!info]
>Si comporta come una [[Politica di scheduling First-In-First-Out (FIFO)|FIFO]]  se i task sono tutti di lunghezze simili

