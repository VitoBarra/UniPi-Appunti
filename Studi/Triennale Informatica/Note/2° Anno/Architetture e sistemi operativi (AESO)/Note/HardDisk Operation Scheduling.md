---
Subject: Architettura E Sistemi Operativi
topic: nota
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


# Tunneling
se si lavora in IpV6 e ci sono dei percorsi che hanno segmenti di rete con ipv4 
![[Pasted image 20230109004908.png]]
per garantire la consegna si utilizza il tunneling ovvero
il datagramma che viaggia con il pv6 prima di passare ad un router ipv4 è incapsulato in un datagramma IPv4. una volta uscito da tunnel si decapsula e torna a viaggiare il datagramma originale 
nel ipv4 del header aggiunto la sorgente sara l indirizzo ipv4 di B e come destinazione E
![[Pasted image 20230109005738.png]]
Se c è Frammentazione nel tunnel viene riassemlato dal router che supporta Ipv6 alla fine del tunnel quindi in questo esempio E 


