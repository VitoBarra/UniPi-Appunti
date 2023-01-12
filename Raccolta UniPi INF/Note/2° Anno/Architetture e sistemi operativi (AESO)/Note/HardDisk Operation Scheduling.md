---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Hard Disk Operation Scheduling
---
un buon algoritmi di scheduling sulle richieste del operazioni sul [[HardDisk Driver(HDD)|disco]] può ottimizzare il tempo i tempi di attesa. questi algoritmi possono essere realizzati sia nel sistema operativo che firmware del dispositivo

## FIFO

questa da poche performance siccome in casi misti memoria sulle tracce esterne e interne portano a lunghe attese.

## Shortest positioning time first (SPTF) or shortest seek time first (SSTF)

un algoritmo gready che cerca di servire la richiesta che più veloce da raggiungere purtroppo pero questo sistema non sempre è ottimale e in più può portare a starvation delle richieste più lontane se arrivano richieste e zone di memoria molto vicino e molto spesso

# Algoritmi di tipo Elevator

- _SCAN_: parte dal più esterno e va vero l interno e torna in dietro facendo cosi prima o poi serve tutte le richieste
- _CSCAN_ : una variante di SCAN che una volta arrivata al centro riparte dalla zona più esterna, questo rende l algoritmo è più migliora il tempo di risposta media siccome si ritrova in una zona dove probabilmente ci sono più richieste, ed è più fair siccome se una richiesta verrà fata appena dietro la testina questa non dovrà aspettare due giri per essere servita ma solo uno
- _R-SCAN_ e _R-CSCAN_: varianti che prendono in considerazione la rotazione del disco e servono anche delle richieste nella direzione opposta, questo per servire delle richieste che contatto al rotazione non chiedono moto tempo per essere servite
