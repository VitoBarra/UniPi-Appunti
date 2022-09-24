---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Far partire un nuovo processo
---


per inizializzare un [[Astrazione dei Processi|processo]] il kernel deve:

- allocare inizializzare il process control block (PCB)
- allocare la memoria del processo
- copiare il programma nella memoria appena allocata
- allocare lo user-stack
- Allocare il Kernel-stack

per eseguire il processo il kernel deve:

- **Copiare gli argomenti nella memoria utente:** quando un processo viene avviato di solito gli vengono passati degli  argomenti che vengono messi alla base dello stack utente
- **Passare  in user-mode:** per passare dal kernel al processo in user-mode viene riutilizzato il codice di ritorno da un interruzione anche se non c è nessuno stato salvato da cui tornare, essenzialmente questo inizializza i registri

poi con una istruzione stub viene chiamato il main, con lo stub si da un punto di ingresso in cui il kernel salta al inizio del programma e chiama una exit al return di quella funzione di inizio. senza dopo il return l user proverebbe a fare una pop nello stack user ma non essendoci nulla andrebbe ad esegui de codice random.
