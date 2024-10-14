---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
tags:
  - AESO
topic: Thread Scheduling
---

# Multi-level feedback queue (MFQ)
---
è una politica in cui si scegliere il task utilizzando una coda di livelli.
ogni livello avrà una priorità un task livello di priorità più alta fra periclasio su i task delle code più basse e i task nello stesso livello vengono eseguite con una politica [[Round Robin|round robin]]. ogni coda ha un quanto di tempo diverso e i livelli a priorità più alta hanno un quanto di tempo più breve rispetto a quelle di livello più basso


i task si muovono nei vali livelli:

- ⬇️ abbassandosi :
    - se portano a termine il proprio quanto di tempo
    - se un task riceve più del suoi fair-share ( periodicamente controllato )
- ⬆️ alzandosi:
    - se un task rilascia volontariamente il processo
    - se deve aspettare una risposta I/O
    - se i task non raggiungono il loro fair-share ( periodicamente controllato )

## Caratteristiche



### Pro

- ha tempo di risposta medio basso siccome approssima [[Politica di Scheduling Shortest Job First (SJF)|SJF]]
- ha un basso overhead come per la [[Politica di scheduling First-In-First-Out (FIFO)|FIFO]]
- evita la starvation
- garantire la fairness approssima il [[Max-Min Fairness]]

### Contro

- complesso da realizzare++

## Workload

### Caso Ottimo

- NESSUNO

### Caso pessimo

- NESSUNO


>[!info ]
questa politica è quella utilizata oggi da Windows, MacOS, e Linux


