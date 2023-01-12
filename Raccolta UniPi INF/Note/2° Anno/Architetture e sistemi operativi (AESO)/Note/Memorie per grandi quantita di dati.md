---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Memorie per grandi quantità di dati
---

queste memorie sono gestirete con una matrice bidimensionale che accetta  $N$ segnali di indirizzo e $M$  di dati. $2^N$ sono il numero di indirizzi esprimibili con $N$  segnali e $M$ la lunghezza della riga, ovvero quanti bit ci sono per indirizzo. $M$ bit vengono detti parola

per descrivere i componenti di memoria ci sono due paramenti

- lunghezza: numero di righe quindi $2^N$
- larghezza: numero di colonne quindi $M$

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 25.png]]

queste memorie sono realizzate con delle celle di bit collegate ad una linea di parola (indirizzo) e linea di bit(dati).

Quando la linea di parola è ALTA, la parola indirizzata può essere letta o scritta. Altrimenti, la linea di bit è disconnessa dalla cella di bit

Per leggere una cella di bit, la linea di bit viene inizialmente lasciata elettricamente fluttuante. Viene quindi attivata la linea di parola, che permette al valore immagazzinato di forzare la linea di bit a 0 o a 1. Per scrivere la cella di bit, invece, la linea di bit viene forzata in modo deciso al valore desiderato. Viene poi attivata la linea di parola, che collega quindi la linea di bit alla cella di bit in cui memorizzare il dato. La linea di bit forzata in modo deciso sovrasta il contenuto della cella di bit, scrivendo il valore voluto nel bit in questione.

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 11.png]]

### Memorie multi-porte

Porte di memoria
Tutte le memorie possiedono una o più porte. Ognuna di queste fornisce un accesso in lettura e/o in scrittura a un indirizzo di memoria. Gli esempi precedenti rappresentavano tutti memorie a una sola porta.
Le memorie multi-porta possono accedere a più indirizzi nello stesso momento
