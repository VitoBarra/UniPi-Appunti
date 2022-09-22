# DeadLock

Un deadlock é  un attesa circolare su di un set di thread

Può accadere in più occasioni:

- Recursive Locking :

    Quando due thread vanno in attesa circolare

    ```c

    //Thread A
    lock1.acquire();
    lock2.acquire();
    lock2.relese();
    lock1.relese();

    //Thread B
    lock2.acquire();
    lock1.acquire();
    lock1.relese();
    lock2.relese();
    ```

- Nested Waiting:

    Un oggetto condiviso che ha acquisito due lock aspetta su un condition variable ma l oggetto che puo fare [sig](http://sig.na)nal ha bisogno di quel lock

    ```c
    // Thread A
    lock1.acquire();
    ...
    lock2.acquire();
    while(need to wait){cv.wait(&lock)}
    ...
    lock2.relese();
    ...
    lock1.relese();

    // Thread B
    lock1.acquire();
    ...
    lock2.acquire();
    ...
    cv.signal();
    lock2.relese();
    ...
    lock1.relese();
    ```


Un caso classico di deadlock è il problema dei filosofi a cena dove ogni filosofo ha bisogno di due bastoncini per mangiare e quindi deve prenderne uno a sinistra e uno a destra ma c è un solo bastoncino per ogni filosofo quindi mentre uno mangia quelli affianco dovranno necessariamente aspettare che il primo finisca e rilasci i bastoncini se voglio fare la stessa cosa

[[9CB27C61-5A69-4561-B92F-7715EF75DFAE.jpeg]]

### Deadlock vs Starvation

Entrambi sono problemi di livness ma la deadlock é una condizione più forte quindi deadlock implica starvation.

## Condizioni necessarie per Deadlock

1. C è un numero finito di thread che possono simultaneamente accedere ad una risorsa
2. Non c é pre-rilascio
3. Un thread aspetta mentre ha già una risorsa (lock)
4. C è un insieme di thread tale che ogni thread aspetti una risorsa mantenuta da un altro thread nel insieme

<aside>
💡 Queste 4 condizione sono necessario ma non sufficienti  per un deadlock.

</aside>

Ad esempio se ci sono più istanze di una sola risorsa la 4 condizione potrebbe essere vera ma non causare un deadlock siccome potrebbe esserci un thread fuori dal ciclo che eventualmente rilascerà una risorsa e sbloccherà il ciclo

[[FCE75DE4-F9E0-41E9-A67F-EB29DC7B54D0.jpeg]]

[[Prevenzione Deadlock]]

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
