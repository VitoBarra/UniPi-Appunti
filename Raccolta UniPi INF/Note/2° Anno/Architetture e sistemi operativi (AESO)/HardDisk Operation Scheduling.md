---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# HardDisk Operation Scheduling
---
un buon algoritmi di scheduling sulle richeste del operazioniu sul disco puo ottimizzare il tempo i tempi di attesa. questi algoritmi possono essere realizati sua nel sistema operativo sia chene  firmware del dispositivo

## FIFO

questa da poche performance siccome in casi mistidi memoria sulle tracce esterne e interne portano a lunghe attese.

## shortest positioning time first (SPTF) or shortest seek time first (SSTF)

un algoritmo gready che cerca di servire la richiesta che piu veloce da ragiungere pultroppo pero questo sistema non sempre è ottimale e in piu puo portare a stavation delle richieste piu lontane se arrivano richieste e zone di memoria molto vicino emolto spesso

# Algoritmi di tipo Elevator

- SCAN: parte dal piu esterno e va vero l interno e torna in dietro facendo cosi prima o poi serve tutte le richieste
- CSCAN : una variante di SCAN che una volta arrivata al centro riparte dalla zona piu esterna, questo rende l algoritmo è piu migliora il tempo di rispostga media siccome si ritrova in una zona dove praobabilmente ci sono piu richieste, ed è piu fair siccome se unarichiesta verar fata appena dietro la testina questa non dovra aspettare due giri per essere servita ma solo uno
- R-SCAN e R-CSCAN: varianti che prendono in considerazione la rotazione del disco e servono anche delle richieste nella direzione opposta, questo per servire delle richieste che contanto al rotazione non chiedono moto tempo per essere servite
