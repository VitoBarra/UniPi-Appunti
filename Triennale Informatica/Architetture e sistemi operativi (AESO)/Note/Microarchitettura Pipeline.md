---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: 
tags:
  - AESO
---
# Pipeline
---
è una [[Microarchitetture|microarchitettura]] a più cicli di _clock_ ovvero ogni [[Istruzioni Machina|istruzione]] viene eseguita più cicli di _clock_  ma utilizza il concetto di [[Forme di Parallelismo#Temporale Pipeline|PipeLine]] per eseguire più istruzioni contemporaneamente

caratteristiche:

- ha bisogno di stato non architetturale (registri non del [[ARM V7|archiettura arm]] quindi registri diversi da r0-r15)
- CLU semplice per lo più semplice con poche parti più complesse rispetto al [[Single Cicle]]
- memoria dati e istruzioni separate

utilizzando più cicli di clock per ogni istruzione il singolo ciclo può essere più breve e le istruzioni brevi verranno completate in meno cicli mentre quelli lunghe nei cicli necessari.

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 27.png]]

[[Dipendenze sulla microarchitettura Pipeline]]

[[Predizioni Salti]]
