---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# DBMS - Sort Delle tabelle nei DB
---
• L’algoritmo più comunemente utilizzato dai DBMS è quello detto di Merge Sort a Z vie (Z-way Sort-Merge) • Supponiamo di dover ordinare un input che consiste di un file di NP pagine e di avere a disposizione solo NB < NP buffer in memoria centrale • L’algoritmo opera in 2 fasi: • Sort interno: si leggono una alla volta le pagine del file; i record di ogni pagina vengono ordinati facendo uso di un algoritmo di sort interno (es. Quicksort); ogni pagina così ordinata, detta anche “run”, viene scritta su disco in un file temporaneo • Merge: operando uno o più passi di fusione, le run vengono fuse, fino a produrre un’unica run

Per semplicità consideriamo il caso base a Z = 2 vie, e supponiamo di avere a disposizione solo NB = 3 buffer in memoria centrale
![[Pasted image 20240116004302.png]]
• Nel caso base Z = 2 si fondono 2 run alla volta • Con NB = 3, si associa un buffer a ognuna delle run, il terzo buffer serve per produrre l’output, 1 pagina alla volta • Si legge la prima pagina da ciascuna run e si può quindi determinare la prima pagina dell’output; quando tutti i record di una pagina di run sono stati consumati, si legge un’altra pagina della run
![[Pasted image 20240116004315.png]]

• Consideriamo per semplicità solo il numero di operazioni di I/O • Nel caso base Z = 2 (e NB = 3) si può osservare che: • Nella fase di sort interno si leggono e si riscrivono NP pagine • Ad ogni passo di merge si leggono e si riscrivono NP pagine (2 * NP) • Il numero di passi fusione è pari a ⎡log2 NP ⎤, in quanto ad ogni passo il numero di run si dimezza • Il costo complessivo è pertanto pari a 2 * NP * ( ⎡ log2NP ⎤ + 1)



• Una prima osservazione è che nel passo di sort interno, avendo a disposizione NB buffer, si possono ordinare NP pagine alla volta (anziché una sola), il che porta a un costo di 2 * NP * ( ⎡ log2 (NP/NB) ⎤ + 1) • Esempio: con NP = 8000 pagine e NB = 3 si hanno ora 208.000 I/O • Miglioramenti sostanziali si possono ottenere se, avendo NB > 3 buffer a disposizione, si fondono NB – 1 run alla volta (1 buffer è per l’output) • In questo caso il numero di passi di fusione è logaritmico in NB – 1, ovvero è pari a 2 * NP * ( ⎡ logNB-1 (NP/NB) ⎤ + 1)

![[Pasted image 20240116004339.png]]



• Oltre che per ordinare le tuple, il Sort può essere utilizzato per: • Query in cui compare l’opzione DISTINCT, ovvero per eliminare i duplicati • Query che contengono la clausola GROUP BY