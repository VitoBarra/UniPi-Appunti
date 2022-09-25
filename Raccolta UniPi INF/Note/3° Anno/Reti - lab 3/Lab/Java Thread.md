---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Java Thread
---


### librerie da usare per la gestione dei thread

- java.lang.Thread


> [!info] Thread Default java
>1. main
>2. Interfaccia utente
>3. [[Garbage colletor]]
 

# Utilizzare thread

## Implementare l’ interfaccia Runnable

l [[interfaccia]] Rubbable mette a disposizione un metodo _Run_() che sarà il metodo lanciato dal thread che deve eseguire quel task.

Proviene dalla libreria :

Java.language

1. Scrivere una classe che implementa l interfaccia Runnable significa creare un task

```java
public class ThreadRunnable {
	public static class MyRunnable implements Runnable {

	public void run() {
		System.out.println("MyRunnable running");
		System.out.println("MyRunnable finished");
	}
}
```

un task può essere passato ad un Thread e invocare il metodo _start_()  per poterlo avviare. Una volta in esecuzione questo invocherà il metodo _Run_() del interfaccia.

```java
public static main()
{
	var newThread = new Thread(new MyRunnable())
	newThread.start();
}
```

>[!note]
 >Creare il task e diverso da creare un thread. Si possono avviare multipli thread a cui si passano i task



## Estendere la classe thread

un modo per Utilizzare i Thread In Java è estendere la calasse Thread e Implementare il metodo _run_()

```java
public class extends Thread
{
 @Override
	public void run()
	{
		System.out.println("MyRunnable running");
		System.out.println("MyRunnable finished");
	}
}
```

 per poi creare un oggetto di quel tipo per poterlo avviare e eseguire il task

```java
public static main()
{
	var newThread = new MyThread()
	newThread.start();
}
```

## scegliere cosa usare

In java non c e [[erederete multipla]] quindi nei casi in cui ho bisogno che una classe possa essere eseguita da un thread ma ho bisogno che estenda anche altro ad esempio gestione eventi

### Errori da evitare

Richiamare Mythread.Run(). Così non si avvia il thread stai solo invocando il metodo.

Bisogna chiamare Thread.Start() segnala alla JVM che il thread puo essere messo in stato di Ready ready


>[!note]
>Thread.currentThread().getName(): Restituisce il nome del thread correntemente in esecuzione


## Thread Demoni
i Thread possno essere settato come "demoni" prima di essere avviati utilizzando la funzione _setDeamon(bool)_. se i thread sono demono il programma non aspetta che questi thread finiscano l esecuzione ma al termine del programma vengono semplicemente chiusi.