# Temporizzazioni

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 11.png]]

## Terminologie

- Fronte di salita: il passaggio da BASSO ad ALTO di un segnale
- Fronte di discesa: il passaggio da ALTO ad  BASSO  di un segnale

in un diagramma temporale viene  viene risportata la risposta transitoria  e gli aventuali ritardi misurati tra il 50% del vari fronti

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 3.png]]

diagramma temporale di una porta buffer

## Ritardi di Propagazione e di contaminazion

### Propagazione

Il ritardo di propagazione indicato con $t_{pd}$ è il tempo massimo che trascorre dal momento in cui avviene un cambiamento nell’ingresso al momento in cui l’uscita (o le uscite) raggiunge il suo valore finale

### Contaminazione

il ritardo di contaminazione indicato con $t_{cd}$ è il tempo minimo che trascorre dal momento in cui cambia un ingresso al momento in cui una qualsiasi uscita comincia il processo di adattamento del
suo valore

Le cause del ritardo nelle reti includono il tempo richiesto per caricare la
capacità elettrica in una rete e la velocità della luce. tpd e tcd possono essere
diversi per una serie di motivi, tra cui:

- diversi ritardi tra salita e discesa
- ingressi e uscite multipli, alcuni più veloci di altri
- reti che rallentano quando si surriscaldano e che lavorano più velocemente
se fredde

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 2 1.png]]

### Percorso critico e percoso minimo

- il percorso critico (critical path) è un percorso che parte da un ingresso e arriva al uscita passando per il piu alto numero di porte e quindi con il piu alto ritardo
- Il percorso minimo (short)è un percorso che parte da un ingresso e arriva al uscita con il che passa per il minimo numero di porte e quindi che ha il ritardo piu basso

    [[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 3 1.png]]


il ritardo di propagazione è dato dalle somme dei ritardi sul percorso critico

il ritardo di contaminazione è dato dalle somme dei ritardi sul percorso minimo

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 4 1.png]]

[[Alee]]

[[Percorso critico e percorso corto]]

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
