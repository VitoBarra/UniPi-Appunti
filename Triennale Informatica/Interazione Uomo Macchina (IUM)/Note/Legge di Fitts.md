---
Course: Interazione Uomo Macchina
topic: nota
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Legge di Fitts
---
la _legge di fitt_ è un modello predittivo  del movimento umano usato primariamente nel _interazione umano-macchina_ e nel ergonomica

questa legge predice che il tempo richiesto per muoversi in un area target è una funzione del rapporto tra la distanza $D$ dal punti di partenza al target e l ampiezza del target $W$

questa legge descrive il tempo sia che ci si sta riferendo al touch con il dito che con un puntatore.

per calcolare il _movement time_ (TM) si ha che 
$$MT = a+b \cdot ID = a+b\cdot \log_{2}\left( \frac{2D}{W} \right)$$
dove
- $a=$ tempo di _start e stop_ del dispositivo (misurato empiricamente per ogni device)
-  $b=$ la velocita del dispositivo (misurato empiricamente per ogni device)
- $D$ la _distanza_ dal punto di inizio al centro del target
- $W$ è l _ampiezza_ del targhe lungo l asse di movimento
![[Pasted image 20230615004600.png]]