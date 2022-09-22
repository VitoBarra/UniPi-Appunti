# Numeri con segno

## Modulo e segno

modulo e segno significa utilizare $N-1$ bit per il modulo del numero e il piu significatavo per espremere il segno, nello specifico $0$  per i positivi e $1$ per i negatvi

### Espressivita

- il range di espressivita è $[-2^{N-1}+1,2^{N-1}-1]$
- numeri DIVERSI rapresentati $2^N-1$

### Problematiche

- non funziona bene per le somme binarie un esempio

    $-5_{10} + 5_{10} = 1101_2  + 0101_2 = 10010_2$ che è divverso da zero e quindi un valore insensato

- si hanno due rapresentazioni per lo 0 avendo la possibilita di esprimere +0 e -0

## Complemento a due

utilizare il complemente a due per esprimere i numeri ralaviti consiste nel utilizare $N-1$ bit per il numero vero e proprio il bit piu significativo rapresenta il segno, per ottenere l invevrso di un numero bisogna fare il **complemento** ( invertire tutti i bit ) di tutti i bit e aggiungere $1$

### Espressivita

- il range di espressivita è $[-2^{N-1},2^{N-1}-1]$
- numeri DIVERSI rapresentati $2^N$

### Osservazioni

- facendo il cmplemento a due su $-2^{N-1}$ si ottiene sempre$-2^{N-1}$
- lo zero ha una solo rapresentazione ed è positivo perche il suo bit piu significativo è $0$
- sommando un numero negativo e uno positivo non si va mai in **overflow**
- per rapresentare un numero con un numero $m$ di bit partendo da un numero gia rapresentato con $n$  bit bisogna estendere il segno mettendo i $m-n$  bit nuovi al valore del segno precedente questo si chiama estensione del sengo

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Conoscenze generali/Numeri Binari/Numeri con segno/Untitled.png]]

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
