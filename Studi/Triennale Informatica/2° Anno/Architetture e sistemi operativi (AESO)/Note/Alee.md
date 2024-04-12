---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Alee
---
## Definizione

un alea sono un problema di [[Temporizzazioni|temporizzazione]] e sono generate da cambiamenti multipli generati da un singolo cambiamento nei segnali di ingresso

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 15 1.png]]

si possono riconoscere con le [[Mappe Di Karnaugh]]

![[Untitled 1 5 1.png]]

e si possono risolvere aggiungente un implicante che valichi i confini dei due implicanti presenti

![[Untitled 2 3 1.png]]

questo metodo di solito non è cosi vantaggioso perché le alee spesso non sono un grande problema siccome basta aspettare il tempo di propagazione per leggere un valore corretto sulle uscite. in più questo metodo risolve il caso del cambiamento di un solo ingresso, se più ingressi dovessero cambiare contemporaneamente potrebbero comunque presentarsi alee

