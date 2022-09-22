# Shortest Job First (SJF)

è una politica in cui si scegliere il task con il tempo rimanente piu breve è puramente teorico siccome per implementarlo servirebbe conoscere la lunghezza dei task ovvero il futuro. per quanto sia teorico questo si puo aprossimare

## Carateristiche



### Pro

- *ottimo* per il tempo di risposta medio

### Contro

- peggiore in per la Varianza
- Non sempre evita la starvation
- non garantisce la fairness

## Workload

### Caso Ottimo

- sempre ottimo per tempo di risposta medio per ogni workload il migliore anche per altri paramentri se è composto da task di lunghezza simile

### Caso pessimo

- nel workload vengono aggiunti spesso task molto piccoli non dando la posibilita a task lunghi di essere eseguiti questi possono andare in starvation

<aside>
💡 Si comporta come una FIFO  se i task sono tutti di lunghezze simili

</aside>
