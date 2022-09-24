---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Forme di Parallelismo
---
### Spaziale (Parallelo)

per realizzare parallelismo spaziale si deve duplicare l hardware e questo permette di fare più compiti contemporaneamente

### Temporale (Pipeline)

il parallelismo temporale si ottiene suddividendo un compito in N passi di tempo idealmente sempre uguale $t$ cosi che mentre un compito viene eseguito e passa per le varie fasi un altro può iniziare le fasi precedenti. si realizza mettendo dei registri tra gli stadi da passare

![[Untitled 22 1.png]]
