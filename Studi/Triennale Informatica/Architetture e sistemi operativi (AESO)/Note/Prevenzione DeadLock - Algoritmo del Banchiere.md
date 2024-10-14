---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---


# Prevenzione DeadLock - Algoritmo del Banchiere
---
|
## Algoritmo del Banchiere

l __algoritmo del banchinare__ è un [[Algoritmi|algoritmo]] progettato da _Dijkstra_ per la [[Prevenzione Deadlock|prevenzione dei deadlock]]   e si basa sul fatto che solo perché un programma può andare in deadlock non significa che lo farà. definisce uno stato safe, unsafe e [[MultiThreading - DeadLock|Deadlock]]. l algoritmo evita che si passi da uno stato safe ad uno unsafe ritardando la concessione di alcune risorse.

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 8 1.png]]

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

>[!note]
questo algoritmo di solito non viene usato nella sua interezza ma vengono usate delle versioni semplificate.
l idea di base può essere utilizzata per capire in che contesti il programma può diventare unsafe