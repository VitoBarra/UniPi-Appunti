# Oblivious Scheduling

è una politica in cui si scegliere il task si utilizza il modello del MLF  e si trattano i singoli thread come se fossero entita separata quindi senza organizare in nessun modo i thread per prendere vantaggio dei altri processori

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 17.png]]

## Carateristiche



### Pro

- ha le caratteristiche del [MLF](../Processore%20singolo%20c6f8a83ef3364c7e9a96c63db574ebfe/Multi-level%20feedback%20queue%20(MFQ)%20e1eeeb4672224abf8e432f78270c8d87.md)

### Contro

- non è consapevole del tipo di lavoro quindi non sfrutta bene il parallelismo del avere piu processori
- è equamente probabile che venga fatto prerilascio di un thread sul [[Percorso Critico]]

## Workload

### Caso Ottimo

- nessuno

### Caso pessimo

- in caso di programmi  [[Bulk Synchronous]], siccome fare prerilascio di un solo thread porta tutti gli altri a dover aspettare il cuo completamento
- in caso di programmi [[Producer-Consumer]], siccome fare prerilascio uno dei produttori manda in stallo l intero programma
- in caso di programmi con molta I/O

<aside>
💡

</aside>
