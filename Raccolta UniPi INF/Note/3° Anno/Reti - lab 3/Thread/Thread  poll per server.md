# Thread  poll per server

## Problematica:

I thread hanno un overhead di gestione (interazione con OS ) e e un cost in termini di risorse sulla memoria siccome ogni thrad ha il suo stack privato e c è  piu“stress” sul garbage collector .

questo può essere un problema di fatto si potrebbe arrivare a pagare più overhead del vantaggio che si ottiene usando piu thread.

[[Raccolta UniPi INF/Note/3° Anno/Reti - lab 3/Thread/Thread poll per server/Untitled.png]]

<aside>
💡 per evitare questo gli OS di solito limitano il numero di Thread per programma

</aside>

[[Raccolta UniPi INF/Note/3° Anno/Reti - lab 3/Thread/Thread poll per server/Untitled 1.png]]

numero di thread limitato dal livello di capacità di kernel thread

“JAVA break” se si usano più thread di quelli supportati dal SO

# Thread Pool

nel caso ci siano molte task e si vorrebbe aprire un thread per task per non pagare l overhead si può utilizzare una threadPool ovvero un set di thread che possono essere riutilizzati.



le ThreadPool sono di più tipi e deferisco sulle politiche di gestione

### Politiche Da scegliere

- Mantenimento: dei thread
    - es.  il numero di thread può variare, come lo fa
- Attivazione: di quali thread
    - es. scelta del thread a cui dare il nuovo task, quando mandarlo in esecuzione (quindi puo essere ritardata rispetto al arrivo)
- Gestione: dei task in arrivo
    - es. li metto in coda, che può essere limitata o illimitata

[[Raccolta UniPi INF/Note/3° Anno/Reti - lab 3/Thread/Thread poll per server/Untitled 2.png]]

### Executor

Gli Executor è un’interfaccia che serve apponto per decidere i parametri della thread pool

```java
public interface Executor{ public void execute(Runnable task)}
public interface ExecutorService extends Executor {...}
```

 La classe Executors è una classe factory che genera i vari ExecutorService implementati di default nel linguaggio.

per passare un task ad una pool basta

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

# Fixed ThreadPool

È un tipo di ThreadPool che utilizza queste politiche

- Mantenimento: può gestire un numero fisso e immodificabile di task inizializzati subito
- Attivazione: associa ad un thread un task appena ce ne uno libero
- Gestione: gestisce i task mettendoli in una coda illimitata implementata dalla classe ***LinkedBlockingQueue***

Creazione del Fixed thread Pool

```java
ExecutorService service = Executors.newFixedThreadPool(10)
```

## Cached ThreadPool

È un tipo di ThreadPool che utilizza queste politiche

- Mantenimento: Gestisce un numero dinamico di thread. diminuiscono se un thread è inattivo per 60 secondi aumentano se non c è ne sono abbastanza per soddisfare le richieste
- Attivazione: associa ad un task ad un Thread appena ce ne uno libero
- Gestione: gestisce i task create un nuovo Thread se non c è ne sono disponibili altrimenti gli ne assegna uno libero

```java
ExecutorService service = Executors.newCacheThreadPool()
```
