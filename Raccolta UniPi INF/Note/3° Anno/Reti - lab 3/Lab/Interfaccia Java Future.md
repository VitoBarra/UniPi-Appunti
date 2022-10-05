---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Interfaccia Java Future
---
l [[interfaccia]] Future è un interfaccia [[Java]] che serve a gestire i risultati dei [[Java Thread|thread]] che eseguono un task implementato con l [[Interfaccia Java Callable]]. Quindi ad ogni oggetto di tipo future è associato un oggetto di tipo Callable

```java
public interface Future 
{
	V get( ) throws...;
	V get (long timeout, TimeUnit) throws...; 
	void cancel (boolean mayInterrupt); 
	boolean isCancelled( );
	boolean isDone( );
 }
```
- _get_(): si blocca fino a che il thread non ha prodotto il valore richiesto e restituisce il valore calcolato 
- _get_ (long timeout, TimeUnit):definisce un tempo massimo di attesa della terminazione del task, dopo cui viene sollevata una TimeoutException 
- _isCancelled_(): verifica se il task è stato cancellato
- _IsDone_(): verifica se il task è stato completato