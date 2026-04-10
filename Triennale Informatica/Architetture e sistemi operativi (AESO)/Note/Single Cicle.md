---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags: AESO
---

# Single Cicle
---
è una [[Microarchitetture|microachitettura]] a _ciclo unico_ ovvero tutte le istruzioni vengono eseguite in un unico _ciclo di clock_

caratteristiche:
- non ha bisogno di stato non architetturale (registri non del [[ARM V7|architettura ARM]] quindi registri diversi da r0-r15)
- CLU semplice siccome è [[Reti Combinatorie|rete combinatoria]]
- memoria dati e istruzioni separate

utilizzando un unico ciclo per ogni istruzione bisogna rendere la lunghezza di questo quanto il tempo necessario ad eseguire l istruzione più lenta. cosi facendo pero le istruzioni brevi verranno eseguite nello stesso tempo di quelle lente

![[IMG - Single Cicle 1.png]]

## Control unit

![[IMG - Single Cicle 2.png]]
