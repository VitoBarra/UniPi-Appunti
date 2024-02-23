---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Executor
---

Gli Executor è un’[[interfaccia]] che serve per la gestione della [[Thread Pool]]

```java
public interface Executor{ public void execute(Runnable task)}
public interface ExecutorService extends Executor {...}
public interface ScheduledExecutorService extends ExecutorService {...}
```


##### Executor Service
è un interfacce estende Executor richiedendo l implementazioni dei metodi di [[ThreadPool Specifiacare il comportamento|gestione della thread pool]]


##### ScheduledExecutorService 
- è un interfacce estende ExecutorService e aggiunge i metodi di gestione della schedulazione della thread Pool 
	-  dopo un certo periodo di tempo (delay) 
	- periodicamente 
- schedule(Runnable command, long delay, TimeUnit unit) 
	- esegue un task Runnable (o Callable) dopo un certo intervallo di tempo 
- _scheduleAtFixedRate_(Runnable(o Callable) command, long initialDelay, long delay, TimeUnit unit) 
	- esegue un task dopo un intervallo iniziale, poi lo ripete periodicamente. 
	- se il tempo di esecuzione del task è maggiore del periodo specificato, le sue seguenti esecuzioni possono essere ritardate. 
- _scheduleWithFixedDelay_(Runnable(o Callable) command, long initialDelay, long delay, TimeUnit unit)
	- esegue un task dopo un intervallo iniziale, poi lo ripete periodicamente con un intervallo dato tra la terminazione di una esecuzione e l'inizio della successiva

## Utilizzo Concreto
 Esiste una [[Design pattern - Factory|classe factory]] chiamata _Executors_ che serve a generare le istanze delle classi che implementano  ExecutorService o ScheduledExecutorService. alcune implementazioni di default del linguaggio [[java]] sono:
 - [[Fixed ThreadPool]]
 - [[Cached ThreadPool]]
 - [[ThreadPool a singolo Thread]]
Di queste c è anche la variante Schedulata
 - [[Scheduled Thread Pool]]
 si può anche [[ThreadPool Specifiacare il comportamento|specificare il comportamento]] voluto

per passare un task ad una pool basta:
```java
public static void main(String[] args) {
 // create the pool
 ExecutorService service = Executors.newFixedThreadPool(10);
 //submit the task for execution
 for (int i =0; i<100; i++)
 {
		service.execute(new Task(i)) } // se NON ha valore di ritorno
		service.submit(new Task(i)) } // se ha valore di ritorno
		System.out.println("Thread Name:"+ Thread.currentThread().getName());
 }
```
per la gestione del risultato _submit_ ritorna un oggetto di tipo [[Interfaccia Java Future|Future]]
![[Pasted image 20221005221938.png]]