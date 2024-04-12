---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Temporizzazioni
---
![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 11 1.png]]

## Terminologie

- Fronte di salita: il passaggio da BASSO ad ALTO di un segnale
- Fronte di discesa: il passaggio da ALTO ad  BASSO  di un segnale

in un diagramma temporale viene  viene riesportata la risposta transitoria  e gli eventuali ritardi misurati tra il 50% del vari fronti

![[Untitled 1 3 1.png]]

diagramma temporale di una porta buffer

## Ritardi di Propagazione e di contaminazione

### Propagazione

Il ritardo di propagazione indicato con $t_{pd}$ è il tempo massimo che trascorre dal momento in cui avviene un cambiamento nell’ingresso al momento in cui l’uscita (o le uscite) raggiunge il suo valore finale

### Contaminazione

il ritardo di contaminazione indicato con $t_{cd}$ è il tempo minimo che trascorre dal momento in cui cambia un ingresso al momento in cui una qualsiasi uscita comincia il processo di adattamento del
suo valore

Le cause del ritardo nelle reti includono il tempo richiesto per caricare la
capacità elettrica in una rete e la velocità della luce. tpd e tcd possono essere
diversi per una serie di motivi, tra cui:

- diversi ritardi tra salita e discesa
- ingressi e uscite multipli, alcuni più veloci di altri
- reti che rallentano quando si surriscaldano e che lavorano più velocemente
se fredde

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 1 1.png]]

### Percorso critico e percorso minimo

- il percorso critico (critica path) è un percorso che parte da un ingresso e arriva al uscita passando per il più alto numero di porte e quindi con il più alto ritardo
- Il percorso minimo (short)è un percorso che parte da un ingresso e arriva al uscita con il che passa per il minimo numero di porte e quindi che ha il ritardo più basso

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3 1 1.png]]


il ritardo di propagazione è dato dalle somme dei ritardi sul percorso critico

il ritardo di contaminazione è dato dalle somme dei ritardi sul percorso minimo

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 4 1 1.png]]
