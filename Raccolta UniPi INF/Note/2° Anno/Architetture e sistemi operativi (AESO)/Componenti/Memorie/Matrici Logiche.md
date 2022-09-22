# Matrici Logiche

le matrici logiche sono porte logiche organizate in modo regolare con collegamenti configurabili

## Matrici logiche Programmatili  hj

la PLA(Programmable Logic Array) realizano funzioni combinatorie a due livelli nella forma somma di prodotti. quindi una matrice di AND seguita da una matrice di OR

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/Matrici Logiche/Untitled.png]]

una Una PLA da M × N × P bit possiede M ingressi, N implicanti e P uscite

Le ROM possono essere viste come casi particolari di PLA. Una ROM da $2^M$ parole $\times N$ bit è semplicemente una PLA a $M \times 2^M \times N$  bit

## Matrici di porte logiche programmabili sul campo

Una FPGA è una matrice di porte logiche riconfigurabile.Le FPGA sono
più potenti e più flessibili rispetto alle PLA perche

- consentono di realizzare sia funzioni combinatorie sia funzioni sequenziali.
- possono realizzare funzioni logiche a più livelli,

Le FPGA moderne integrano altre caratteristiche utili preconfigurate, come moltiplicatori, ingressi e uscite ad alta velocità, convertitori di dati inclusi i convertitori analogico-digitali, memorie RAM di grandi dimensioni e processori.

le FPGA vengono costruite come una matrice di elementi logici (LE, Logic Element) configurabili, chiamati anche blocchi logici configurabili (CLB,
Configurable Logic Block). Ogni LE può essere configurato in modo da eseguire funzioni combinatorie o sequenziali. Gli LE sono circondati da elementi di ingresso/uscita (IOE, Input/Output Element) per interfacciarsi al mondo esterno.
Gli IOE connettono gli ingressi e le uscite degli LE ai piedini esterni del chip.
Gli LE possono essere connessi ad altri LE o a degli IOE attraverso canali di
instradamento programmabili.

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/Matrici Logiche/Untitled 1.png]]

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/Matrici Logiche/Untitled 2.png]]

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
