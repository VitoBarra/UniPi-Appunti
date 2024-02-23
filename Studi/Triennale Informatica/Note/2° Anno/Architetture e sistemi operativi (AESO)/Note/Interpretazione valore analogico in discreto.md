---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Interpretazione valore analogico in discreto
---

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 5.png]]

Perché l’uscita del generatore sia interpretata in maniera corretta all’ingresso
del ricevitore, è necessario che sia $V_{OL} < V_{IL}$  e $V_{OH} > V_{IH}$. In questo modo,
anche se l’uscita del generatore viene alterata da una certa quantità di rumore,
l’ingresso del ricevitore è comunque in grado di riconoscere il livello logico
corretto. Il margine di rumore (NM da noise margin) è la quantità di rumore
che può essere aggiunta all’uscita nella peggiore delle ipotesi per far sì che

il segnale riesca ugualmente a essere interpretato come un ingresso valido.
Come si può vedere nella Figura 1.23, i margini di rumore basso e alto sono
rispettivamente

$NML= VIL – VOL$
$NMH = VIH – VOH$
