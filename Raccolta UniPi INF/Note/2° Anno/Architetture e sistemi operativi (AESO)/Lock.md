---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Lock
---
le lock servono a garantire la mutua esclusione utile per gestire la  [[Sincronizzazione di oggetti condivisi]]

per eseguire un pezzo di codice chiamata sezione critica bisogna fare un acquire e una relese sul lock che delimita il pezzo di codice

```c
lock.acquire()
...
//sezione critica
...
lock.relese()
```

  i [[Astrazione Thread|thread]] che vogliono eseguire la sezione critica del codice devono prima cercare di ottenere la lock  se ci riescono eseguono quel pezzo di codice e poi rilasciano il lock. se non riescono a fare l acquire perché é stato fatta dal un altro thread che non ha ancora rilasciato il lock allora thread viene messo in stato d attesa su quel lock e verrai rimessi in stato di READY quando il lock verrà rilasciato

## Implementazione Lock

### Uniprocessore

nel singolo processo i thread possono essere interrompe solo da un interruzione quindi l acquire e la relese vengono implementate lavorando su le interruzioni e per dare la nozione di attesa si lavora con lo schedulatore.

acquire:

```c
LockAcquire()
{
	Disable_enterupt();
	if(value == BUSY)
	{
		waiting.add(myTCB);
		suspend();
	}
	else value = BUSY

	Enable_enterupt()

}
```

Relese:

```c
LockRelese()
{
	Disable_enterupt();
	if(!waiting.Empty())
	{
		thTCB=waitig.remove();
		readyList.Append(thTCB);
	}
	else value = FREE

	Enable_enterupt()
}
```

un implementazione inefficiente potrebbe essere anche solo abilitando e disabilitando le interruzioni. problemi con le interruzioni provenienti da I/O

### MultyProcessore

nel caso di multiprocessore ci potrebbero essere delle acquire contemporaneamente si più processori da problemi siccome se entrambi leggono contemporaneamente in valore del lock e lo trovano aperto entrambi lo prendono non garantendo quindi la mutua esclusione

Acquire:

```c
LockAcquire()
{
	Disable_enterupt();
	Spinlock.aquire()
	if(value == BUSY)
	{
		waiting.add(myTCB);
		suspend(Spinlock);
	}
	else  value = BUSY;

	spinlock.relese()
	Enable_enterupt()

}
```

Relese:

```c
LockRelese()
{
	Disable_enterupt();
	Spinlock.aquire()

	if(!waiting.Empty())
	{
		thTCB= waitig.remove();
		readyList.resume(thTCB);
	}
	else value = FREE

	spinlock.relese()
	Enable_enterupt()

}
```

# Spin-lock

servono per fare attesa attiva utilizza delle  [[Istruzioni Machina|istruzioni assembly]] speciali che atomicamente  controllano se una locazione è un dato valore e se è quello setta il valore di quella locazione, questo serve siccome cosi facendo c è un solo lock che lavora su quella locazione alla volta

un altra istruzione speciale e la EXCH che atomicamente scambia due valori e si può usare per implementare le spin-lock

Acquire:

```c
SpingLock_acquire()
{
	R = BUSSY
	while(R == BUSSY)
		EXCH(R,Lock)
}
```

Relese:

```c
SpingLock_Relese()
{
	Write(FREE,Lock);
	Memory_barrier()
}
```

la [[barriera di memoria]] serve per assicurarsi che la scrittura dell free sul lock avvenga prima che ne possano avvenire altre per questioni legate ai delay messi sulle scritture in memoria. questo assicura che tutti possano leggere subito che il lock sia diventato FREE
