---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Prevenzione Deadlock
---
ci sono vari approcci per evitare deadlock.

- **cambiando o limitando il comportamento del programma**: cambiando il programma si possono pervenire le [[DeadLock#Condizioni necessarie per Deadlock|condizioni necessarie per il deadlock]]
    - **risorse limitate**: dando più risorse si potrebbero in stanziare dinamicamente ma porterebbe e possibili casi di esaurimento memoria che potrebbe portare ad un successivo lock
    - **no prerilascio**: **implementanto un sistema di pre-rilascio**
    - **in attesa mentre mantiene risorese**: rilascio delle risorse prima di chiamare in un altro modulo oppure possono ristrutturare gli oggetti per chiamare altri oggetti condivisi solo se non si sta mantenendo nessun altro lock
    - **attesa circolare**: ordinando i lock con dei lock ordinati si puo fare in modo di non generare attese circolare un esempio è in una tabbella hash dove cè un lock per ogni slot numerando. nelle operazioni tipo  **changeKeys(item, k1, k2)** si prenderà in ordine prima il lock della casella più alta e poi quella più bassa cosi se un altro thread dovrà aspettare lo fara solo solla casella alta evitando cosi l attesa circolare che si sarebbe verificata altrimenti
- **predendo il futuro**: se possiamo sapere prima che un azione (acquire) manderà il programma in deadlock prossimo interromperla momentaneamente
- **riconosci e recupera**: un altro sistema è quello di far accadere il deadlock e una volta riconosciuto restaurare uno stato precedente non ancora in deadlock e sperare non risucceda ****

## Algoritmo del Banchiere

è un algoritmo progettato da Dijkstra e si basa sul fatto che solo perché un programma può andare in deadlock non significa che lo farà. definisce uno stato safe, unsafe e deadlock. l algoritmo evita che si passi da uno stato safe ad uno unsafe ritardando la concessione di alcune risorse.

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 8 1.png]]

### Stati

- Safe: in questo stato per ogni sequenza di richieste di risorse  ne esiste almeno una che garantisce che prima o poi tutte le richieste vengano soddisfatte
- Unsafe: c è almeno una una sequenza di richieste future che porta ad un deadlock
- Deadlock: il sistema ha almeno un deadlock

### Implementazione

utilizza la seguente calasse come stato

```cpp
class ResourceMgr{
 private:
	 Lock lock;
	 CV cv;
	 int r; // Number of resources
	 int t; // Number of threads
	 int avail[]; // avail[i]: instances of resource i available
	 int max[][]; // max[i][j]: max of resource i needed by thread j
	 int alloc[][]; // alloc[i][j]: current allocation of resource i to thread j
	 ...
 }
```

e processa le richieste mantenendo il programma in uno stato safe

```cpp
// Invariant: the system is in a safe state.
 ResourceMgr::Request(int resourceID, int threadID) {
	 lock.Acquire();
	 assert(isSafe());
	 while (!wouldBeSafe(resourceID, threadID)) {cv.Wait(&lock);}

	 alloc[resourceID][threadID]++;
	 avail[resourceID]--;
	 assert(isSafe());
	 lock.Release();
 }
```

una funzione che controlla se dare quella data risorsa a quel thread lascia il programma in uno state safe o no

```cpp
// Hypothetically grant request and see if resulting state is safe.
bool ResourceMgr::wouldBeSafe(int resourceID, int threadID)
{
	bool result = false;
	avail[resourceID]--;
	alloc[resourceID][threadID]++;

	if (isSafe()) result = true;

	avail[resourceID]++;
	alloc[resourceID][threadID]--;
	return result;
}
```

la funzione che controlla se il sistema  è in uno stato Safe

```cpp
// A state is safe iff there exists a safe sequence of grants that are sufficient
// to allow all threads to eventually receive their maximum resource needs.
bool ResourceMgr::isSafe()
{
	int j;
	int toBeAvail[] = copy avail[];
	// need[i][j] is initialized to max[i][j] - alloc[i][j]
	int need[][] = max[][] - alloc[][];
	bool finish[] = [false, false, false, ...]; // finish[j] is true
	// if thread j is guaranteed to finish
	while (true)
	{
		j = any threadID such that:
		(finish[j] == false) && forall i : need[i][j] <= toBeAvail[i];
		if (no such j exists)
		{
			if (forall j: finish[j] == true) return true;
			else return false;
		}
		else
		{
			// Thread j will eventually finish and return its current allocation to the pool.
			finish[j] = true;
			forall i : toBeAvail[i] = toBeAvail[i] + alloc[i][j];
		}
	}
}
```

<aside>
💡 questo algoritmo di solito non viene usato nella sua interezza ma vengono usate delle versioni semplificate.
l idea di base può essere utilizzata per capire in che contesti il programma può diventare unsafe

</aside>

---

# individuare e recuperare da un deadlock

se i casi in cui i deadlock sono rari allora conviene non pagare l overhead per prevenirli, lasciarli accadere e recuperare da quelli nel modo più trasparente possibile.

### Transazioni

le transazioni sono un meccanismo per recuperare fare l undo  di un set di dati toccati nella transazione stessa lasciarli in uno inconsistente. realizzato mantenendo una copia interna dei dati e lavorando su quelli

ha un interfaccia di questo tipo

- **BeginTransaction()**: è il punto di inizio dove viene salvato lo stato dei dati al inizio della transazione
- **EndTransaction()**: il punto di fine transazione in cui se è andata buon termine questa esegue il commit sui dati altrimenti RollBack
- **Commit()**: salva i dati modificati nella transazione
- **RollBack()**: ripristina lo stati dei dati a come se la transazione non fosse mai iniziata

## Individuare Deadlock

per individuare se c è un deadlock si può controllare quanto tempo sta passando e decidere se passa tempo che c è un [[DeadLock]], può dare falsi positivi ma non è un gran problema se il costo di recupero è basso

un altro sistema quando c è una sola istanza di ogni risorsa è usare i grafi

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 2 1.png]]

se nel grafo che rappresenta i thread e le risorse c è un ciclo allora siamo in [[DeadLock]]. se le risorse sono multyistanza il ciclo diventa una condizione necessaria ma non sufficiente per essere in deadlock

un altro modo per capire è la variazione di Coffman, Elphick, and Shoshani del metodo IsSafe() del algoritmo del banchiere

Another solution, described by Coffman, Elphick, and Shoshani in 1971 is a variation of
Dijkstra’s Banker’s Algorithm. In this algorithm, we assume we no longer know max[][], so
we cannot assess whether the current state is safe or whether some future sequence of
requests can force deadlock. However, we can look at the current set of resources, granted
requests, and pending requests and ask whether it is possible for the current set of
requests to eventually be satisfied assuming no more requests come and all threads
eventually complete. If so, there is no deadlock (although we may be in an unsafe state);
otherwise, there is a deadlock.

```cpp
// A state is safe iff there exists a safe sequence of grants that would allow
 // all threads to eventually receive their maximum resource needs.
 //
 // avail[] holds free resource count
 // alloc[][] holds current allocation
 // request[][] holds currently-blocked requests
bool ResourceMgr::isDeadlocked()
{
	int j;
	int toBeAvail[] = copy avail[];
	bool finish[] = [false, false, false, ...]; // finish[j] is true if thread
	// j is guaranteed to finish
	while(true)
	{
		j = any threadID such that (finish[j] == false)
				&& (forall i: request[i][j] <= toBeAvail[i]);
		if (no such j exists)
		{
			if (forall j: finish[j] == true) return false;
			else return true;
		}
		else
		{
			// Thread j *may* eventually finish and
			// return its current allocation to the pool.
			finish[j] = true;
			forall i: toBeAvail[i] = toBeAvail[i] + alloc[i][j];
		}
	}
}
```

### Recuperare da Deadlock

per recuperare dal un deadlock individuato si utilizzano le [[Transazioni]]

- Thread RollBack: si scelgono dei thread vittima e si fanno fallire avviando un RollBack
- Thread Reset: sbloccato il deadlock i thread scelti come vittima vengono riavviati

durante le transizioni gli altri thread non possono vedere i valori intermedi delle copie dei dati e questo è realizzato con i lock in due fasi a

per scegliere quali thread scegliere come vittima si segue una politica di anzianità in modo da garantire che prima o poi tutti possano arrivare a completamento.

si sceglie quindi il più giovane che prima o poi diventerà vecchie s metterà di essere scelto
