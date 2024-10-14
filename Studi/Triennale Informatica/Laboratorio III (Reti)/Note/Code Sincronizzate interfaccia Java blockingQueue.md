---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Code Sincronizzate Interfaccia Java blockingQueue
---

	Package: java.until.cuncurrent
	
La __blockingQueue__ È un [[interfaccia]] di una coda [[Thread Safe]].
- adatta per il pattern [[Producer-Consumer|Produttore-Consumatore]] 
![[Pasted image 20220925200204.png]]
Implementata da :
- _ArrayBlockingQueue_ : Coda limitata è implementata con un array e singolo lock, quindi niente operazioni concorrenti e la dimensione della coda è limitata 
- ![[Pasted image 20220925202008.png]]
- _LinkedBlokignQueue_: Coda che può essere _Illimitata_ che significa che può avere un limite che specifichiamo noi o altrimenti il massimo è Integer._MAX_VALUE_ è implementata con una [[Struttura dati - Lista linkata]] e usa più lock quindi so possono fare operazione sugli elementi concorretemene. ad ogni inserzione si crea un nuovo oggetto e tende ad occupare più memoria rispetto alla ArrayBlockingQueue
- ![[Pasted image 20220925201957.png]]

|         | __Throw Exception__ | __Special value__ | __block__   | __TimesOut__                 |
| ------- | --------------- | ------------- | ------- | ------------------------ |
| __Insert__  | add(o)          | offer(o)      | put(o)  | offer(o,timeout,timeunit |
| __Remove__  | remove(o)       | poll(o)       | take(o) | pool(timeout,timeunit)   |
| __Examine__ | element()       | peek()        |         |                          |
