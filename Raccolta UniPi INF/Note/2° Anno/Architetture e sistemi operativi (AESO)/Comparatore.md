---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Comparatore
---
serve per controlalre se due valori sono uguali è ed raliato con una serie di [[Porte Logiche#Porte Negate6b|NXOR]] e un [[Porte Logiche#Porta And|AND]]

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Z-Media/Untitled 15.png]]

questo restituisce solo l ugualianza per minore e magire si utilizza un sotrattore e si va a controlare il segno del risultato

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Z-Media/Untitled 1 6.png]]

se A è magiore di B allora il segno sara positivo altrimenti il contrario

questo sitema non lavora bene in caso di overflow
