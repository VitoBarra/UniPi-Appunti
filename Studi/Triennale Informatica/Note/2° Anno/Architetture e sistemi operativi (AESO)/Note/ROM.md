---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# ROM
---
Una [[Memorie|memoria]] a sola lettura (ROM, Read Only Memory) memorizza un bit come presenza o assenza di un transistore

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 18.png]]

il pallino rappresenta un uno mentre l assenza di questo uno 0.

una rom è una rete combinatoria a due livelli. siccome ci sono tutti i mintermine (per indicare le linee) si utilizza un decoder e le linee di dato ad uno si collegano ad un OR. questo significa che una ROM può realizzare qualsiasi funzione realizzabile a [[Logica a due Livelli|due livelli]]


### PROM e EPROM EEPROM

nonostante il nome le ROM possono essere riscritte

le  EPROM (Programmable ROM ) possono essere scritte una volta sola siccome sono realizzate con dei [[fusibili]]. il fusibili bruciato contiene un 1 mentre quello integro uno 0.

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 9.png]]

le EPROM (Eresable PROM) sono  rom realizzate con gate sommersi che non sono fisicamente connessi alla linea di bit finche non gli viene passata appositamente una carica che sposta gli elettroni e connette la linea di bit. queste sono “cancellabili ” perché se esposte a luce ultravioletta si possono respingere gli [[elettroni]] e quindi scollegare il gate dalla linea d bit

le EEPROM (Electrically Eresable PROM) utilizzano lo stesso principio delle EPROM ma hanno dei circuiti integrati che permettono di cancellare le celle di memoria e riprogrammarle senza l utilizzo degli UV

### LookUp table
le ROM si possono utilizzare per realizzare qualsiasi funzione logica ad $N$ ingressi con $M$ uscite. questo perché la ROM stessa diventa una lookUp table che rappresenta quella funzione

