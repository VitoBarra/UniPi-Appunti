---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Varianti Flip-Flop
---


## con abilitazione

un flip-flop con abilitazione è un normale [[Flip-flop D]] con l aggiunta di un segnale che se falso ignora il segnale del CLK e non fa cambiare il valore de uscita finale. si può realizzare in più modi:

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 21.png]]

è utile se il valore va cambiato solo in specifici momento e non ad ogni giro di clock

## Resettabili

un flip-flop resettabile è un normale [[Flip-flop D]] con un segnale che forza il valore in uscita a 0 a prescindere dal valore di D possono essere di due tipi

- sincroni: resettano a 0 quando il fronte del clock sale
- asincroni: resettano a 0 a prescindere dal clock

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 12.png]]

Flip-flop con reset attivo basso

comodi quado di deve forzare una valore 0

può essere sia attivo basso (ha effetto con il valore BASSO) che attivo alto (ha effetto con il valore ALTO)a seconda del se c é un Not o no sul segnale di reset
