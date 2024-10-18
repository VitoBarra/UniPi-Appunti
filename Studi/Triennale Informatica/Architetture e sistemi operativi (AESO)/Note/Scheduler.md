---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Scheduler
---
lo scheduling la scelta tra i [[Astrazione Thread |Thread]] pronti da mandare in esecuzione

le politica di scelta dette (di scheduling) devono avere queste proprietà:

- essere **working-conservative**: non lasciare il processore con dei tempi senza lavoro altrimenti qualsiasi altra politica sarebbe più efficiente
- Evitare la **Starvation**: mancanza di progresso di thread
- garantire **Fairness**: quantità di tempo dedicato ad ogni processo

ci sono vari parametri che variano con la scelta di uno o l altra politica di scheduling

- Response time (or delay). The user-perceived time to do some task.
- Predictability. Low variance in response times for repeated requests.
- Throughput. The rate at which tasks are completed
- Scheduling overhead. The time to switch from one task to another.
- average responce time

le varie politiche possono variare di efficacia a seconda di due parametri

- **Workload**: che sta ad indicare l insieme dei task da schedulare
- **Tipo Di task**:
    - Compute-Bound: passa la maggior parte del tempo sul processore
    - I/O-Bound: passa l maggior parte dei tempo ad aspettare la risposta delle I/O