---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Memory Cache lookup
---

## Cache Completamente associativa

In una cache completamente associativa  la ricerca si fa comparando l adress  con ogni entry della cache contemporaneamente restituisce il dato se combaciano

![[9C3BA86D-23C1-4099-9291-930979363527.jpeg]]

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 4.png]]

Questo è non pratico siccome ha bisogno di un comparatore ad ogni entry quindi scala male al  aumentare della dimensione della cache

## Cache a mappatura diretta

Con una cache  a mappatura diretta a la ricerca si esegue hashando l indirizzo da cui prender il dato e comparandoli con la entry raggiunta con il valore del hash

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 1.png]]

![[A4290F4B-BBE5-458A-B034-8980EC43EA0E.jpeg]]

Questo per quanto sia veloce non è sempre pratico siccome può succerei Che più indirizzi hashano alla stessa posizione.

## Cache set associative

Con una cache set associative è una cache con più repliche di blocchi di cache, l entry viene ragniate con il valore hashato in tutte le repliche e in quel entry viene confrontato l indirizzo se combacia restituisce i il dato

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 1.png]]

![[631C493D-589D-4F2A-A805-FD32D52C7B34.jpeg]]

![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3 1.png]]

Questo sistema è un buon compromesso tra cache a mappatura diretta e una completamente associativa perché di essere quasi veloci come la prima  e utilizzando meno hardware della seconda.

![[7A219756-106A-4D8C-AA0F-77B8A7A3B8F3.jpeg]]
