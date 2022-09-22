# Domande Esame

Domande di oggi dei 4 esami di AESO, più o meno complete, tranne forse qualcosa dell'ultimo esame dove ero più distratto. Ho provato a scriverle più in italiano di quanto le dica marcod.

1.

Come si implementa in architettura l'esecuzione di istruzioni condizionali?
Cosa succede quando la condizione è vera? e quando è falsa?
Scrivi la tabella di verità di un demultiplexer che manda 1 bit su 4 uscite
Quanti libelli di logica combinatoria servono?
Supponendo un solo livello di cache data la probabilità di hit, calcolare il tempo medio di accesso alla memoria.
cosa succede se si aggiunge un secondo livello di cache?
Differenza tra attesa attiva e non attiva nella sincronizzazione (lock)
Ho bisogno di una lista per i processi in attesa? Se sì perché?
Dimmi un argomento che ti ricordi bene della seconda parte del corso (a piacere)->Gestione della memoria(segmentazione, base and bound, paging)
Nel caso della segmentazione che componenti firmware servono per implementarla?
Quale componente serve per fare il confronto per non uscire dal bound?

1.

Come avviene la traduzione da indirizzo logico a fisico nel caso di paging?
Cosa trovo nella tabella delle pagine?
Come scriveresti in assembler una procedura per la traduzione dell'indirizzo? dato in R0 l'indirizzo della page table e in R1 l'indirizzo logico a 32 bit
Sarebbe molto costoso fare 4 5 istruzioni assembler ogni traduzione dell'indirizzo, qual è invece la strategia che si usa? [TLB]
Tabella di verità e funzionamento di un encoder a 4 ingressi
Come lo avresti scritto in Verilog?
Nello scheduling abbiamo visto 3 stati: ready, waiting, exec. Descrivi come avvengono le transizioni tra stati.
Nello specifico cosa succede nel passaggio tra lo stato ready e quello exec?
Dato un disco visto già come sequenza di blocchi, come si organizza un FS FAT?

1.

Come si stabilisce la lunghezza del ciclo di clock di una rete sequenziale? (di Moore)
Cambia qualcosa se la rete invece è di Mealy?
Cos'è una dipendenza logica sul controllo? (Processore Pipeline)
Quando può accadere questa situazione?
Come si fa la predizione del salto?
Fai un esempio di salto preso facile da prevedere e salto invece su cui non si riesce a dire molto.
Quali sono alcuni metodi per prevenire lo stallo? (lock)
Cos'è l'attesa circolare? Perchè acquisire i lock in ordine serve a prevenirla?
Cambia qualcosa se sono semafori?
In Multithreading implementato in spazio utente, un thread si blocca (ad esempio su una sem.P() ), cosa succede?
Questo [Il fatto che si blocca tutto il processo] aumenta o diminuisce la probabilità di stallo?

1.

Se non ci fosse l'istruzione branch and link, come implementeresti la chiamata a procedura?

Comporre diverse componenti logiche per lavorare su dati di dimensione maggiore può aumentare il ritardo di stabilizzazione. Fare un esempio in cui questo avviene e un esempio in cui non aviene.
[Avviene con Full Adder, non avviene con MUX]
Supponi di voler sommare 4 numeri ad 8 bit, quali componenti hardware useresti per farlo nel modo più veloce possibile?
Qual è il meccanismo di funzionamento delle system call?
Cos'è il working set? Fai due esempi di utilizzo del concetto di working set.
Come faccio a capire quali sono le pagine del working set?
