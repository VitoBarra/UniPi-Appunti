# Sistemi Operativi

il sitema operativo è una layer software che gestisce le risorse del computer

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Sistemi Operativi/Untitled.png]]

il sistema operativo è il softwere piu a basso livello che fornisce una astrazione e una protezione a tutto il sistema ed è in esecuzione in un environment separato rispetto alle altre aplicazioni che utente vengono in modo isalato in un contesto dato dal kernel, questo permette di prevenire danni e dare al programma piu espressivita mascherando le limitazione hardwere

il sistema operativo deve svolgere 3 funzioni pricipali

- Albitraggio :
    - Alocazione risorse: gestire quale e quando dare una data risorsa a quale processo tra i processio che runnano sull stressa macchina
    - isolamento: i vari programmi vengono isolati in modo che un errore in un programma non disturbi gli altri prgramo e il sistema operativo, questa cosa è chiamata fault Isolation, questo permette anche di protegersi da virus. Viene realizato limitando le capacita dei programmi rispetto l hardwere
    - Comunicazione: isolando i programmi si pone il problema di come farli comunicare. il sistema operativo deve permettere delle comunicazioni controllate tra i processi
- illusionista : il sistema operativo da l illusione ai programmi di lavorare  con delle risorse che non sono fisicamente presenti
    - Virtualizazine: il sistema  da ai programmi una astrazione per lavorare come se il programma avesse infinia memoria e un precessore dedicato, astrae anche come è fisicamente fatto l hardwere permettendo ai programmi di lavorare con dei file piuttosto che con i blocchi di momoria specifici del dispositivo

    si possono virtualizare anche interi sistemi operativi  comodo per debuggarte

- collante : il sitema fornisce delle interfacce di condivisione di risorse tra i vari processi, per sempio un file puo essere scritto da un programma e letto da un altro. un altro caso interessante è il caso del I/O dove il sitema  fornisce un layer di astrazione cosi che ogni programma non ha bisogno di conoscere lo specifico dispositivo o anche un interfaccia generica per i vari tipo di interfacce network (WiFi, Ethernet, bluetooth)

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Sistemi Operativi/Untitled 1.png]]

[[Scelta di un sistema operativo]]

[[Astrazione Kernel]]

[[Organizazione di sistema operativo]]

---

Status : #NotSet

Tag: [Aeso](../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
