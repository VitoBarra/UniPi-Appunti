---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Sistemi Operativi
---


il sistema operativo è una layer software che gestisce le risorse del computer

![[Untitled 30.png]]

il sistema operativo è il softwere più a basso livello che fornisce una astrazione e una protezione a tutto il sistema ed è in esecuzione in un environment separato rispetto alle altre aplicazioni che utente vengono in modo insalato in un contesto dato dal kernel, questo permette di prevenire danni e dare al programma più espressività mascherando le limitazione hardware

il sistema operativo deve svolgere 3 funzioni principali

- Arbitraggio :
    - Allocazione risorse: gestire quale e quando dare una data risorsa a quale processo tra i processi che runnano sul stressa macchina
    - isolamento: i vari programmi vengono isolati in modo che un errore in un programma non disturbi gli altri programmi e il sistema operativo, questa cosa è chiamata fault Isolation, questo permette anche di proteggersi da virus. Viene realizzato limitando le capacita dei programmi rispetto l hardware
    - Comunicazione: isolando i programmi si pone il problema di come farli comunicare. il sistema operativo deve permettere delle comunicazioni controllate tra i processi
- illusionista : il sistema operativo da l illusione ai programmi di lavorare  con delle risorse che non sono fisicamente presenti
    - Virtualizzazione: il sistema  da ai programmi una astrazione per lavorare come se il programma avesse infinita memoria e un precessore dedicato, astrae anche come è fisicamente fatto l hardware permettendo ai programmi di lavorare con dei file piuttosto che con i blocchi di memoria specifici del dispositivo

    si possono virtualizzare anche interi sistemi operativi  comodo per debuggare

- collante : il sistema fornisce delle interfacce di condivisione di risorse tra i vari processi, per esempio un file può essere scritto da un programma e letto da un altro. un altro caso interessante è il caso del I/O dove il sistema  fornisce un layer di astrazione cosi che ogni programma non ha bisogno di conoscere lo specifico dispositivo o anche un interfaccia generica per i vari tipo di interfacce network (Wi-Fi, Ethernet, Bluetooth)

![[Untitled 1 13 1.png]]
