# Far partire un nuovo processo

per inizializare un processo il kernel deve:

- allocare einizializare il process control block (PCB)
- allocare la memoria del porcesso
- copiare il programma nella memoria appena allocata
- allocare lo user-stack
- Allocare il Kernel-stack

per esegure il processo il kernel deve:

- **Copiare gli argomenti nella memoria utente:** quando un precesso viene avviato di solito gli vengono passati degli  argomenti che vengono messi alla base dello stack utente
- **Passare  in user-mode:** per passare dal kernel al processo in user-mode viene riutilizzato il codice di ritorno da un interruzione anche se non c è nessuno stato salvato da cui tornare, essenzialmente questo inizializza i registri

poi con una istruzione stub viene chiamato il main, con lo stub si sda un punto di ingresso in cui il kernel salta al inizio del programma e chiama una exit all return di quella funzione di inizio. senza dopo il return l user proverebbe a fare una pop nello stack user ma non essendoci nulla andrebbe ad esegui de codice random.

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
