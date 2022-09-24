---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Single Cicle
---


è una [[Microarchitetture|microachitettura]] a ciclo unico ovvero tutte le istruzioni vengono eseguite in un unico ciclo di clock

caratteristiche:

- non ha bisogno di stato non architetturale (registri non del [[ARM V7|architettura ARM]] quindi registri diversi da r0-r15)
- CLU semplice siccome è [[Reti Combinatorie|rete combinatoria]]
- memoria dati e istruzioni separate

utilizzando un unico ciclo per ogni istruzione bisogna rendere la lunghezza di questo quanto il tempo necessario ad eseguire l istruzione più lenta. cosi facendo pero le istruzioni brevi verranno eseguite nello stesso tempo di quelle lente

![[Untitled 29.png]]

## Control unit

![[Untitled 1 12 1.png]]
