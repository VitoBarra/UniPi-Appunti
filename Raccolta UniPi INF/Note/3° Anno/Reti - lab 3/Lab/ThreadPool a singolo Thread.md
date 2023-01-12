---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3 MOC]]

# ThreadPool a singolo Thread
---


- un singolo thread 
- equivalente ad invocare un [[Fixed ThreadPool]] di dimensione 1 
- utilizzo: assicurare che i thread del pool vengano eseguiti nell'ordine con cui si trovano in coda (sequenzialmente) 

```java
ExecutorService service = Executors.SingleThreadExecutor(10)
```
