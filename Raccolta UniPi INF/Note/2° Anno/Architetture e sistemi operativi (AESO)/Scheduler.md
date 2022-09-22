# Scheduler

lo scheduling la sceltra tra i thread pronti da mandare in esecuzione

le politica di scelta dette (di scheduling) devono avere queste proprieta:

- essere **working-conservative**: non lasciare il processore con dei tempi senza lavoro altrimenti qualsiasi altra politica sarebbe piu efficente
- Evitare la **Starvation**: mancanza di progresso di thread
- garantire **Fairness**: equalita di tempo dedicato ad ogni processo

ci sono vari parametri che variano con la scelta di uno o l altra politica di scheduling

- Response time (or delay). The user-perceived time to do some task.
- Predictability. Low variance in response times for repeated requests.
- Throughput. The rate at which tasks are completed
- Scheduling overhead. The time to switch from one task to another.
- average responce time

le varie politiche possono fariare di efficacia a seconda di due parametri

- **Workload**: che sta ad indicare l insieme dei task da schedulare
- **Tipo Di task**:
    - Compute-Bound: passa la magior parte del tempo sul processore
    - I/O-bound: passa l magior parte dei tempo ad aspettare la risposta delle I/O

[[Processore singolo]]

[[Multy-Processore]]

---

Status : #NotSet

Tag: [Aeso](../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
