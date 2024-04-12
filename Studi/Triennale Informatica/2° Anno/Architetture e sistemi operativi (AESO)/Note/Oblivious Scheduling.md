---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Oblivious Scheduling
---


è una politica di [[Scheduler|schedilung]] per il multyproccessore in cui si scegliere il task si utilizza il modello del MLF  e si trattano i singoli thread come se fossero entità separata quindi senza organizzare in nessun modo i thread per prendere vantaggio dei altri processori

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 17 1.png]]

## Carateristiche



### Pro

- ha le caratteristiche del [[Multi-level feedback queue (MFQ)|MFQ]]

### Contro

- non è consapevole del tipo di lavoro quindi non sfrutta bene il parallelismo del avere piu processori
- è equamente probabile che venga fatto prerilascio di un thread sul [[Percorso critico]]

## Workload

### Caso Ottimo

- nessuno

### Caso pessimo

- in caso di programmi  [[Bulk Synchronous]], siccome fare prerilascio di un solo thread porta tutti gli altri a dover aspettare il cui completamento
- in caso di programmi [[Producer-Consumer]], siccome fare prerilascio uno dei produttori manda in stallo l intero programma
- in caso di programmi con molta I/O
