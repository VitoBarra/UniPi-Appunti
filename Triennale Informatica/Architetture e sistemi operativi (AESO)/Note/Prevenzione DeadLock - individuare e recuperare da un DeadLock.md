---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---

# Prevenzione DeadLock - individuare e recuperare da un DeadLock
---
se i casi in cui i [[MultiThreading - DeadLock|deadlock]] sono rari allora conviene non pagare l overhead per [[Prevenzione Deadlock|prevenirli]], lasciarli accadere individuarli e poi recuperare da quelli nel modo più trasparente possibile.

### Transazioni

le transazioni sono un meccanismo per recuperare fare l undo  di un set di dati toccati nella transazione stessa lasciarli in uno inconsistente. realizzato mantenendo una copia interna dei dati e lavorando su quelli

ha un interfaccia di questo tipo

- **BeginTransaction()**: è il punto di inizio dove viene salvato lo stato dei dati al inizio della transazione
- **EndTransaction()**: il punto di fine transazione in cui se è andata buon termine questa esegue il commit sui dati altrimenti RollBack
- **Commit()**: salva i dati modificati nella transazione
- **RollBack()**: ripristina lo stati dei dati a come se la transazione non fosse mai iniziata

## Individuare Deadlock

per individuare se c è un deadlock si può controllare quanto tempo sta passando e decidere se passa tempo che c è un [[MultiThreading - DeadLock|DeadLock]], può dare falsi positivi ma non è un gran problema se il costo di recupero è basso

un altro sistema quando c è una sola istanza di ogni risorsa è usare i grafi

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 1 2 1.png]]

se nel grafo che rappresenta i thread e le risorse c è un ciclo allora siamo in [[MultiThreading - DeadLock|deadlock]]. se le risorse sono multyistanza il ciclo diventa una condizione necessaria ma non sufficiente per essere in deadlock

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
