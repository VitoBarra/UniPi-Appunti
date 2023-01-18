---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# ThreadPool Specificare il comportamento
---
per personalizzare il funzionamento della [[Thread Pool]] si implementa l [[interfaccia]] [[Thread Pool#Executor|ExecutorService]] una il costruttore classe _ThreadPoolExecutor_ a cui si passano i seguenti parametri:
```java
import java.util.concurrent.*;
public class ThreadPoolExecutor implements ExecutorService 
{
public ThreadPoolExecutor(int CorePoolSize, int MaximumPoolSize, long keepAliveTime,
				TimeUnit unit, BlockingQueue workqueue, RejectedExecutionHandler handler)
}
```
- Configurazione Comportamento:
	- __CorePoolSize__:
		- numero minimo di thread attivi 
		- Attivabile: subito con _PrestartAllCoreThread_() o "on demand" quando arrivano le task
	- __MaxPoolSize__: Numero massimo di Thread Che possono essere attivato nella thread pool
	- __KeepLiveTIme__: 
		- é un valore in tempo dopo il quale un Thread Inattivo viene ucciso
		- vale per thread _non_ appartenenti al Core
			- si può invertire questo comportamento con _AllowCoreThreadTimeOut_(bool) <- questa funzione può lanciare un eccezione
			- ![[Pasted image 20220925204219.png]]
- Politica di Accettazione Task:
	- __WorkQueue__: è una struttura dati necessaria per memorizzare gli eventuali tasks in attesa di esecuzione
	-  Se la coda e piena si può scegliere cosa fare con i task che arrivano 
	- __[[RejectedExecutionHandler]]__: handler che gestisce l [[Le eccezioni|eccezione]] di rigetto che viene sollevata quando la coda non può accettare un nuovo task 
		- ![[Pasted image 20220925221655.png]]
	



## Esempi

| __Parametri__   | __[[Fixed ThreadPool]]__          | __[[Cached ThreadPool]]__ |
| ----------- | ----------------------------- | --------------------- |
| __CoreMaxSize__ | valore passato al costruttore | 0                     |
| __MaxPoolSize__ | stesso valore CoreMaxSize     | Integer.MaxValue      |
| __KeepAlive__   | 0 secondi                     | 60 Secondi            |
| __QueueType__   | linkedBlokingQueue            | SynchronousQueue      | 
