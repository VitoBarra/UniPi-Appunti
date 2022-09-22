# Thread

### librerie da usare per la gestione dei thread

- java.lang.Thread

<aside>
💡 Thread Default java

- main
- Interfaccia utente
- Garbage colletor
</aside>

# Utilizare thread

## Implementare l’ interfaccia Runnable

l interfaccia Rubbable mette a disposizione un metodo Run() che sara il metodo lanciato dal thread che deve eseguire quel task.

Proviene dalla libreria :

Java.language

Scrivere una classe che implementa l intrfaccia Runnable significa creare un task

```java
public class ThreadRunnable {
	public static class MyRunnable implements Runnable {

	public void run() {
		System.out.println("MyRunnable running");
		System.out.println("MyRunnable finished");
	}
}
```

un task può essere passato ad un Thread e invocare il metodo [[stat]]()  per poterlo avviare. Una volta in esecuzione questo invocherà il metodo Run() del interfaccia.

```java
public static main()
{
	var newThread = new Thread(new MyRunnable())
	newThread.start();
}
```

<aside>
💡 Creare il task e diverso da creare un thread. Si possono avviare multipli thread a cui si passano i task

</aside>

## Estendere la classe thread

un modo per Utilizare i Thread In Java è estendere la calasse Thread e Implementare il motodo run()

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

In java non c e erederieta multipla quindi nei casi in cui ho bisogno che una classe possa essere eseguita da un thread ma ho bisogno che estenda anche altro ad esempio gestione eventi

### Errori scemi

Richiamare Mythread.Run(). Così non si avvia il thread stai solo invocando il metodo.

Bisogna chiamare Thread.Start() segnala alla JVM che il thread puo essere meso in stato di Ready ready

# Note

Thread.currentThread().getName(): Restituisce il nome del thread correntemente in esecuzione

[[Thread  poll per server]]
