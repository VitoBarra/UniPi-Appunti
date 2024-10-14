---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
tags:
  - AESO
topic: Thread Scheduling
---

# Round Robin
---
è una politica di [[Scheduler|scheduling]] in cui si dividono i task in Time Slice detti "quanti di tempo" questi quanti di tempo devono essere scelte con cura siccome fare cambiare da un task ad un altro aggiunge overhead sia per fare lo [[Switch di contesto]] che per caricare in [[Architetture e sistemi operativi (AESO)]] quello che serve al thread scelto; quindi scegliere un quanto ti tempo troppo corto significa aggiungere molto overhead e sceglierne uno troppo lungo significa far aspettare molto dei task.

## Caratteristiche



### Pro
- garantisce la fairness
- evita la starvation

### Contro

- Ha molto Overhead
- il quanti di tempo devono essere scelti accuratamente
- efficacia variabile con workload diversi

## Workload

### Caso Ottimo
- il workload é composto da task di lunghezza variabile, in questo caso approssima [[Politica di Scheduling Shortest Job First (SJF)|SJF]]

### Caso pessimo
- il workload è composto da task di lunghezza simile

![[Untitled 18 1.png]]

- c è un mix di task I/O-bounded e Compute-Bound questo perche i task I/O-bounded dovranno aspettare il loro prossimo turno dopo una richiesta al I/O

![[Untitled 1 7 1.png]]



>[!info] __Confronti con altre politiche__
Se si setta un quanto di tempo lungo un istruzione il Round Robin approssima il comportamento del [[Politica di Scheduling Shortest Job First (SJF)|SJG]] ma essendoci overhead è molto più lento
se invece è lungo quanto il task più lungo allora si comporta come una [[Politica di scheduling First-In-First-Out (FIFO)|FIFO]]
>>[!abstract]
>>è ideale quando serve un progresso predicibile e stabile tipo il buffering di un video su YouTube




