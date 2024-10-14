---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Flip-flop D
---
il flip-flop viene realizzato con due [[Memorie - Latch D]] sincronizzato con un clock complementare, questo componente si aggiorna solo sul fronte di salita del clock ed é molto utile per gestire la [[Temporizzazioni]]

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 20.png]]

con il clock BASSO il primo [[Memorie - Latch D]] chiamato master è trasparente e il secondo opaco in questo modo il master è in grado di ricevere il valore di D e ma l’uscita dello latch Slave non cambia. Quando il clock passa ad ALTO il master diventa opaco e non cambia il suo valore e funge da buffer per lo slave che ora è trasparente e può aggiornare la sua uscita prendendo D dal uscita del primo latch