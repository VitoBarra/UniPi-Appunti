---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Fixed ThreadPool
---


È un tipo di [[Thread Pool]] che utilizza queste politiche

- _Mantenimento_: può gestire un numero fisso e immodificabile di task inizializzati subito
- _Attivazione_: associa ad un thread un task appena ce ne uno libero
- _Gestione_: gestisce i task mettendoli in una coda illimitata implementata dalla classe ***LinkedBlockingQueue***

Creazione della Fixed thread Pool

```java
ExecutorService service = Executors.newFixedThreadPool(10)
```
![[Pasted image 20220925222229.png]]