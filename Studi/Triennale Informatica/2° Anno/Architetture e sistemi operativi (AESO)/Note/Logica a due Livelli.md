---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Logica a due Livelli 
---


Gli ingressi vengono indicati a sinistra (o in alto) dello schema.
• Le uscite vengono indicate a destra (o in basso) dello schema.
• Le porte logiche, quando possibile, sono disegnate in modo che i segnali
vadano da sinistra a destra.
• I fili dritti sono preferibili ai fili con troppi angoli: fili a zigzag richiedono
uno sforzo mentale maggiore per seguirne il percorso, invece di concentrare
l’attenzione a ciò che fa la rete.
• Fili che arrivano a una giunzione a T sono collegati tra loro.
• Un punto disegnato dove due fili si incrociano indica che quei fili sono collegati tra loro.
• Fili che si incrociano, ma che non presentano un punto disegnato all’incrocio

espressione esempio

$$
Y = \overline{A}
\overline{B}
\overline{C}
+ A\overline{B}\overline{C}
+ A\overline{B}C
$$

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 12 1.png]]

questa è una rete a due livelli di logica siccome ha una serie di AND collegati ad una serie di OR, questa molto utile per progettare siccome rispecchia esattamente la formula somma di prodotti ma si tende a fare una progettazione a più livelli siccome da la possibilità di ridurre l hardware, migliorando quindi la velocita, il costo e il consumo.
