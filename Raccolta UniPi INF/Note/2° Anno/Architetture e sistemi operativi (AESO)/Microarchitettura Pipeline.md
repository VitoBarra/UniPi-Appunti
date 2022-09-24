---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Pipeline
---

è una microarchitettura a più cicli di clock ovvero ogni istruzione viene eseguita più cicli di clock  ma utilizza il concetto di [[Forme di Parallelismo#Temporale Pipeline|PipeLine]] per eseguire più istruzioni contemporaneamente

caratteristiche:

- ha bisogno di stato non architetturale (registri non del [[ARM V7|archiettura arm]] quindi registri diversi da r0-r15)
- CLU semplice per lo più semplice con poche parti più complesse rispetto al [[Single Cicle]]
- memoria dati e istruzioni separate

utilizzando più cicli di clock per ogni istruzione il singolo ciclo può essere più breve e le istruzioni brevi verranno completate in meno cicli mentre quelli lunghe nei cicli necessari.

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 27.png]]

[[Dipendenze sulla microarchitettura Pipeline]]

[[Predizioni Salti]]
