---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Comparatore
---
è un [[Componenti|componente]] e serve per controllare se due valori sono uguali è ed realizzato con una serie di [[Porte Logiche#Porte Negate6b|NXOR]] e un [[Porte Logiche#Porta And|AND]]

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 15.png]]

questo restituisce solo l uguaglianza per minore e maggiore si utilizza un sottrattore e si va a controllare il segno del risultato

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 6.png]]

se A è maggiore di B allora il segno sarà positivo altrimenti il contrario

questo sistema non lavora bene in caso di overflow
