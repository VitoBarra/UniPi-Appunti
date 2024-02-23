---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Java Monitor
---
è un meccanismo di [[Sincronizzazione di oggetti condivisi]] ad alto livello garantisce la mutua esclusione con dei [[Sincronizzazione MultiThreading - Lock]] impliciti o espliciti nel oggetto e la coordinazione con un meccanismo simile alle [[Condition Variable|variabili condizionali]].
ogni oggetto in [[java]] ha un monitor
questi si usano quei metodi dove c è bisogno della gestione del oggetto condiviso per indicare questo si aggiunge il qualificatore _synchronized_ 
```java
	public synchronized Object consume() 
```
quando un thread invocherà questo metodo tenterà di prendere la lock
![[Pasted image 20221005224326.png]]
in questi tipo di motodi si possono invocare:
- void _wait_() 
	- sospende il thread fino a che un altro thread invoca una notify() /notifyAll() sullo stesso oggetto. 
	- implementa una “attesa passiva” del verificarsi di una condizione 
	- rilascia la lock sull'oggetto 
- void _notify_() 
	- sveglia un singolo thread in attesa su questo oggetto 
	- nop se nessun thread è in attesa
- void _notifyAll_() 
	- sveglia tutti i thread in attesa su questo oggetto, che competono per riacquisire della lock

se lo si fa al di fuori di questo tipo di metodi si solleva [[Le eccezioni|l eccezione]] *__IllegalMonitorException__*