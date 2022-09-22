# Max-Min Fairness

è una politica in cui si scegliere il task prendendo il task che ha meno tempo accumulato sul processore e la permanenza sul processore dura un time slice.

se un processo fa prerilascio volontario prima della fine del tempo allora redistribuisce il tempo avanzato a tutti i processi ancora in esecuzione massimizando cosi il minimo di tempo dato ad i processi.

## Carateristiche



### Pro

- ottimo per Fairness
- evita starvation

### Contro

- alto overhead

## Workload

### Caso Ottimo

- funziona bene in casi di task misti Compute-Bound e I/O-bound

### Caso pessimo

- NESSUNO

<aside>
💡

</aside>
