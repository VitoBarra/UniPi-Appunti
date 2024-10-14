---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Interfaccia Java Callable
---

l [[interfaccia]] callable è un interfaccia [[java]]  simile al [[Java Thread#Implementare l’ interfaccia Runnable|interfaccia runnable]] l interfaccia mette a disposizione il metodo _T call_() che Può Restituire valori e sollevare eccezioni. 
```java
public interface Runnable { void run();}
```

1. Scrivere una classe che implementa l interfaccia Callable
```java
public static class MyCallable implements Callable<T>
{1
	public T call() 
	{
		System.out.println("Mycallable running");
		System.out.println("Mycallable finished");
		return 0;
	}
}	
```





## Passare un callable ad un normale thread
uno oggetto callable non può essere passato direttamente ad un [[Java Thread|thread]] perche accetta solo le classi che implementano l [[Java Thread#Implementare l’ interfaccia Runnable|interfaccia runnable]] ma c è una classe concreta che implementa sia runnable che callable ovvero [[Classe FutureTask | FutureTask]], questa siccome implementa runnable può essere passato ad un thread

```java
public static main()
{
	var FutureTask = new FutureTask<T>(new MyCallable<T>());  
	var newThread = new Thread(FutureTask);
	newThread.start();
}
```

> [!question]
> va testato
