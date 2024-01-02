---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Normalizzazione di schemi relazionali -Dipendenze multivalore
---
nella [[Normalizzazione di schemi relazionali|teoria della normalizazione]] oltre le anomalie di _[[Schemi relazionali - Dipendenze funzionali|dipendenza funzionali]]_ cè ne un altra di un altro tipo che riguarda i casi in cui ci sono _proprieta multi valore indipendenti_

per risolvere questo problema va estesa la teoria della normalizzazione con
1. una nuova dipendenza tra i dati, _dipendenza multi valore_
2. estendere la _[[Schemi relazionali - Dipendenze funzionali derivate|dipendeza derivata]]_ alla dipendenza multi valore
3. nuove [[Regole di inferenza|regole di inferenza]] _corrette e complete_ per la derivazione
4. esiste la nozione di [[Schemi Relazionali - Decomposizione di schemi|decomposizione]] che preserva _dati e dipendenze_
5. è stata definita una nuova forma normale detta _[[Forme normali - Quarta forma normale|quarta forma normale]]_ (4NF) che generalizza la forma [[Forme Normali - Boyce-Codd|BCNF]]
6. Algoritmo di normalizzazione per la _quarta forma normale_ con stesse proprieta del algoritmo per BCNF

