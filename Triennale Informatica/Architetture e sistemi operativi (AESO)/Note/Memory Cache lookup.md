---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags: AESO
---

# Memory Cache lookup
---

## Cache Completamente associativa

In una cache completamente associativa  la ricerca si fa comparando l adress  con ogni entry della cache contemporaneamente restituisce il dato se combaciano

![[IMG - Memory Cache lookup 1.jpeg]]

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Memory Cache lookup 2.png]]

Questo è non pratico siccome ha bisogno di un comparatore ad ogni entry quindi scala male al  aumentare della dimensione della cache

## Cache a mappatura diretta

Con una cache  a mappatura diretta a la ricerca si esegue hashando l indirizzo da cui prender il dato e comparandoli con la entry raggiunta con il valore del hash

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Memory Cache lookup 3.png]]

![[IMG - Memory Cache lookup 4.jpeg]]

Questo per quanto sia veloce non è sempre pratico siccome può succerei Che più indirizzi hashano alla stessa posizione.

## Cache set associative

Con una cache set associative è una cache con più repliche di blocchi di cache, l entry viene ragniate con il valore hashato in tutte le repliche e in quel entry viene confrontato l indirizzo se combacia restituisce i il dato

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Memory Cache lookup 5.png]]

![[IMG - Memory Cache lookup 6.jpeg]]

![[UniPi-Appunti/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/IMG - Memory Cache lookup 7.png]]

Questo sistema è un buon compromesso tra cache a mappatura diretta e una completamente associativa perché di essere quasi veloci come la prima  e utilizzando meno hardware della seconda.

![[IMG - Memory Cache lookup 8.jpeg]]
