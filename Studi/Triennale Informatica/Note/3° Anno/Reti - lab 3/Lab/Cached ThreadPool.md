---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Cached ThreadPool
---


È un tipo di [[Thread Pool]] che utilizza queste politiche

- _Mantenimento_: Gestisce un numero dinamico di thread. diminuiscono se un thread è inattivo per 60 secondi aumentano se non c è ne sono abbastanza per soddisfare le richieste
- _Attivazione_: associa ad un task ad un Thread appena ce ne uno libero
- _Gestione_: gestisce i task create un nuovo Thread se non c è ne sono disponibili altrimenti gli ne assegna uno libero

```java
ExecutorService service = Executors.newCacheThreadPool()
```


![[Pasted image 20220925222204.png]]