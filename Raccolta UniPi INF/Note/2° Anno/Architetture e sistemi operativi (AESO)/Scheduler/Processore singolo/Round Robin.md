# Round Robin

è una politica in cui si dividono i task in TimeSlice detti quanti di tempo questi quanti di tempo devono essere scelte con cura siccome fare cambiare da un task ad un altro aggiunge overhead sia per fare lo switch che per caricare in chache quello che serve al thread scelto; quindi scegliere un quanto ti tempo troppo corto significa aggiugnere molto overhead e sceglierne uno troppo lungo significa far aspettare molto dei task.

## Carateristiche



### Pro

- garantisce la fairness
- evita la starvation

### Contro

- Ha molto Overhead
- il quanti di tempo devono essere scelti accuratamente
- efficacia variabile con workload diversi

## Workload

### Caso Ottimo

- il workload é composto da task di lunghezza variabile, in questo caso aprossima SJF

### Caso pessimo

- il workload è composto da task di lunghezza simile

    [[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Scheduler/Processore singolo/Round Robin/Untitled.png]]

- c è un mix di task I/O-bounded e Compute-Bound questo perche i task I/O-bounded dovranno aspettare il loro prossimo turno dopo una richiesta al I/O

    [[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Scheduler/Processore singolo/Round Robin/Untitled 1.png]]


<aside>
💡 Se si setta un quanto di tempo lungo un istruzione il Round Robin aprossima il comportamento del SJG ma essendoci overhead è molto piu lento
se invece è lungo quanto il task piu lungo allora si comporta come una FIFO

</aside>

<aside>
🛠 è ideale quando serve un progresso predicibile e stabile

</aside>
