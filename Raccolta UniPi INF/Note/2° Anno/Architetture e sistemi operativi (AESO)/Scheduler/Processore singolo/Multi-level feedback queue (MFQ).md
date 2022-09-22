# Multi-level feedback queue (MFQ)

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

## Carateristiche



### Pro

- ha tempo di risposta medio basso siccome approssima [SJF](Shortest%20Job%20First%20(SJF)%20af2f70595327486caf0bdc69a8e79d5f.md)
- ha un basso overhead come per la [FIFO](First-In-First-Out%20(FIFO)%20225eae1f95774e86b44941e2c34d6767.md)
- evita la starvation
- garantire la fairness approssima il [[Max-Min]]

### Contro

- complesso da realizzare++

## Workload

### Caso Ottimo

- NESSUNO

### Caso pessimo

- NESSUNO

<aside>
⚙ questa politica è quella utilizata oggi da Windows, MacOS, e Linux

</aside>
