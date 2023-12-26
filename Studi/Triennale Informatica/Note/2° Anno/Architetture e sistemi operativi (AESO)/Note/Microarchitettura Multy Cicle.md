---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Microarchitettura Multy Cicle
---


è una [[Microarchitetture|microarchitettura]] a a più cicli di clock ovvero ogni [[Istruzioni Machina|istruzione]] viene eseguita più cicli di clock

caratteristiche:

- ha bisogno di stato non architetturale (registri non del architettura ARM quindi registri diversi da r0-r15)
- CLU complessa siccome è una [[Macchine a stati finiti|FSM]]
- memoria dati e istruzioni unica

utilizzando più cicli di clock per ogni istruzione il singolo ciclo puoi essere più breve e le istruzioni brevi verranno completate in meno cicli mentre quelli lunghe nei cicli necessari

![[Untitled 26 1.png]]


![[Untitled 1 10 1.png]]

la control unit è una [[Macchine a stati finiti| Macchine a stati finiti]]
![[Untitled 2 4 1.png]]
