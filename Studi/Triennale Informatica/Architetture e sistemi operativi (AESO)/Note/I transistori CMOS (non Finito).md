---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# I transistori CMOS (non Finito)
---


![[62E46717-0C2D-4769-85B0-9C6C5C0C388B.jpeg]]

La Figura 1.32 mostra lo schema di una porta NOT costruita con transistori
CMOS. Il triangolo in basso indica la terra (GND) mentre la barra piatta in
alto indica VDD; queste due abbreviazioni sono omesse negli schemi successivi. Il transistore nMOS, N1, è connesso tra GND e l’uscita Y, mentre il transistore pMOS, P1, è connesso tra VDD e l’uscita Y. I gate di entrambi i transistori
sono controllati dall’ingresso, A.
Se A = 0, N1 è spento e P1 è acceso. Di conseguenza, Y è connesso a VDD
ma non a GND, e viene innalzato al valore logico 1. P1 trasmette bene un 1.
Se invece A = 1, N1 è acceso e P1 è spento, e Y viene abbassato al valore logico 0. N1 trasmette correttamente uno 0. Se si esamina il comportamento del
circuito tramite la tabella delle verità di Figura 1.12, si nota facilmente che il
circuito altro non è che una porta NOT
