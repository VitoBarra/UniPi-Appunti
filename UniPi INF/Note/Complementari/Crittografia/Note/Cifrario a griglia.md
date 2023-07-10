---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a griglia
---
è un [[Cifrari storici|cifrario storico]] che secondo la [[Classificazione di cifrari|classificazione]] è un cifrario a _trasposizione_

#### Definizione
si basa sul idea di avere una pagina $P$ _scritta ad hoc_ per contenere il messaggio e una griglia di dimensione $q\times q$ con $q$ pari e con $s = \cfrac{q^{2}}{4}$ celle _trasparenti_ e le restanti opache.

il processo di decrittazione si fa ponendo sulla pagina P la griglia e scrivendo cosi i primi $s$ caratteri, poi _ruotando_ la griglia di $90°$ in senso orario  si possono scrivere i successivi $s$ _caratteri_.
le celle trasparenti devono essere scelte in modo che non ricomprino mai la stessa due volte durante le rotazioni.
![[Pasted image 20230705160230.png]]

se abbiamo che il la lunghezza del messaggio $|m| < 4s$ gli spazzi non usati vengono riempiti a caso mentre se sono $|m|>4s$  si divide il messaggi in piu pagine.

#### Spazio delle chiavi
fissiamo una cella  $a_{0}$ e indichiamo con $a_{2},a_{3},a_{4}$ le celle raggiungibili tramite rotazione. Rifacendo questo procedimento per $s=\cfrac{q^{2}}{4}$ scegliendo sempre celle diverse da quelle gia scelte precedentemente otteniamo $s$ gruppi di celle, questi gruppi insieme raggiungono tutte le celle _una ed una sola volta_

per ogni gruppo abbiamo 4 elementi e possiamo sceglierne uno arbitrariamente, cosi facendo andiamo a costruire una _griglia_ che sarà la chiave del cifrario. 
Di conseguenza abbiamo che  $|K|=4^s=2^{q^{s}/2}$ che è il numero di _griglie_ possibili.
 