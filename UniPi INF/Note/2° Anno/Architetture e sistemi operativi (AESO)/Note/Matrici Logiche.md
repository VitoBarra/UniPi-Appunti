---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Matrici Logiche
---
le matrici logiche sono porte logiche organizzate in modo regolare con collegamenti configurabili

## Matrici logiche Programmatili

la PLA(Programmable Logic Array) realizzano [[Logica a due Livelli|funzioni combinatorie a due livelli]] nella forma somma di prodotti. quindi una matrice di AND seguita da una matrice di OR

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 22.png]]

una Una PLA da M × N × P bit possiede M ingressi, N implicanti e P uscite

Le [[ROM]] possono essere viste come casi particolari di PLA. Una [[ROM]] da $2^M$ parole $\times N$ bit è semplicemente una PLA a $M \times 2^M \times N$  bit

## Matrici di porte logiche programmabili sul campo

Una FPGA è una matrice di porte logiche riconfigurabile. Le FPGA sono
più potenti e più flessibili rispetto alle PLA perché

- consentono di realizzare sia funzioni combinatorie sia funzioni sequenziali.
- possono realizzare funzioni logiche a più livelli,

Le FPGA moderne integrano altre caratteristiche utili riconfigurate, come moltiplicatori, ingressi e uscite ad alta velocità, convertitori di dati inclusi i convertitori analogico-digitali, memorie RAM di grandi dimensioni e processori.

le FPGA vengono costruite come una matrice di elementi logici (LE, Logic Element) configurabili, chiamati anche blocchi logici configurabili (CLB,
Configurable Logic Block). Ogni LE può essere configurato in modo da eseguire funzioni combinatorie o sequenziali. Gli LE sono circondati da elementi di ingresso/uscita (IOE, Input/Output Element) per interfacciarsi al mondo esterno.
Gli IOE connettono gli ingressi e le uscite degli LE ai piedini esterni del chip.
Gli LE possono essere connessi ad altri LE o a degli IOE attraverso canali di
instradamento programmabili.

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 13.png]]


![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 7.png]]