---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---

# Prevenzione Deadlock
---
ci sono vari approcci per evitare deadlock.

- **cambiando o limitando il comportamento del programma**: cambiando il programma si possono pervenire le [[MultiThreading - DeadLock#Condizioni necessarie per Deadlock|condizioni necessarie per il deadlock]]
    - **risorse limitate**: dando più risorse si potrebbero in stanziare dinamicamente ma porterebbe e possibili casi di esaurimento memoria che potrebbe portare ad un successivo lock
    - **no periclasio**: **implementano un sistema di pre-rilascio**
    - **in attesa mentre mantiene risorse**: rilascio delle risorse prima di chiamare in un altro modulo oppure possono ristrutturare gli oggetti per chiamare altri oggetti condivisi solo se non si sta mantenendo nessun altro lock
    - **attesa circolare**: ordinando i lock con dei lock ordinati si puo fare in modo di non generare attese circolare un esempio è in una [[Hash Table|tabella hash]] dove cè un [[Sincronizzazione MultiThreading - Lock|lock]] per ogni slot numerando. nelle operazioni tipo  **changeKeys(item, k1, k2)** si prenderà in ordine prima il lock della casella più alta e poi quella più bassa cosi se un altro thread dovrà aspettare lo farà solo solla casella alta evitando cosi l attesa circolare che si sarebbe verificata altrimenti

- __Deadlock advoidance__ : basati su regole di aquisizione di lock
	- [[Prevenzione Deadlock - Consecutive Two phase locking|Consecutive Two Phase Lock]]
- **prevendo il futuro**: se possiamo sapere prima che un azione (acquire) manderà il programma in deadlock prossimo interromperla momentaneamente
	- [[Prevenzione DeadLock - Algoritmo del Banchiere|Algoritmo del banchiere]]
- **riconosci e recupera**: un altro sistema è quello di far accadere il deadlock e una volta riconosciuto restaurare uno stato precedente non ancora in deadlock e sperare non risucceda ****
	- [[Prevenzione DeadLock - individuare e recuperare da un DeadLock|individuare e recuperare da un DeadLock]]

