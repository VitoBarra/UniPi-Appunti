---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO FileNotFound 
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Multi-level feedback queue (MFQ)
---


è una politica in cui si scegliere il task utilizando una coda di livelli ogni livello avra una priorita un task livello di priorita piu alta fra prerilascio su i task delle code piu basse e i task nello stesso livello vengono eseguite con una politica round robin. ogni coda ha un quanto di tempo diverso e i livelli a priorita piu alta hanno un quanto di tempo piu breve rispetto a quelle di livello piu basso

[[Multi-level feedback queue (MFQ]]%20e1eeeb4672224abf8e432f78270c8d87/Untitled.png)

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


