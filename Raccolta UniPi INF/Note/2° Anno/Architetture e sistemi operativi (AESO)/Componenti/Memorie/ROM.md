# ROM

Una memoria a sola lettura (ROM, Read Only Memory) memorizza un bit
come presenza o assenza di un transistore

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/ROM/Untitled.png]]

il pallino rapresenta un uno mentre l assenza di questo uno 0.

una rom è una rete combinatoria a due livelli. siccome ci sono tutti i mintermini (per indicare le linee) si utilizza un decoder e le linee di dato ad uno si collegano ad un OR. questo significa che una ROM puo realizare qualsiasi funzione relizabile a due livelli



### PROM e EPROM EEPROM

nonostante il nome le ROM possono essere riscritte

le  EPROM (Programmable ROM ) possono essere scritte una volta sola siccome sono realizate con dei fusibili. il fusibili bruciato contiene un 1 mentre quello integro uno 0.

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/ROM/Untitled 1.png]]

le EPROM (Eresable PROM) sono  rom realizate con gate sommersi che non sono fusicamente connessi alla linea di bit finche non gli viene passata appositamente una carica che sposta gli eletroni e connette la linea di bit. queste sono “cancellabili ” perche se esposte a luce ultravioletta si possono rispongere gli eletroni e quindi scollegare il gate dalla linea d bit

le EEPROM (Electrically Erasable PROM) utilizzano lo stesso principio delle EPROM ma hanno dei circuiti integrati che permettono di cancellare le celle di memoria e riprogrammarle senza l utilizzo degli UV

### LookUp table

le ROM si possono utilizare per realizare qualsiasi funzione logica ad $N$ in gressi con $M$ uscite. questo perche la ROM stessa diventa una lookUp table che rapresenta quella funzione

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
