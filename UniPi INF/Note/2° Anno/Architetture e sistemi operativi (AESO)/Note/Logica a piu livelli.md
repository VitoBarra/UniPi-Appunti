---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Logica a più livelli
---


la logica a più livelli è piu complessa della [[Logica a due Livelli]] ma ci sono delle tecniche per semplificarla riducendo cosi anche l hardware

## Spingere le bolle

Nel paragrafo 1.7.6 si è già accennato al fatto che le reti CMOS preferiscono le
porte NAND e NOR alle porte AND e OR. Tuttavia, derivare un’espressione
a partire da una rete a più livelli con porte NAND e NOR non è un compito
semplice, come si deduce dalla Figura 2.33, che mostra una rete a più livelli
la cui funzione non è immediatamente chiara. Spingere le bolle è molto utile
in contesti come questo, per ridurre il numero di bolle e facilitare l’identificazione della funzione. In aggiunta ai principi elencati nel paragrafo 2.3.3, per
spingere le bolle si tengano presenti le seguenti linee guida.
• Iniziare all’uscita della rete e lavorare a ritroso verso gli ingressi.
• Spingere qualsiasi bolla sia posizionata sull’uscita finale indietro verso gli
ingressi, in modo da poter leggere l’espressione in termini di uscita diritta
(per es. Y) piuttosto che in termini di uscita negata (Y
-).
• Lavorando a ritroso, disegnare ogni porta in modo tale da cancellare le bolle.
Se la porta corrente ha una bolla sull’ingresso, disegnare la porta che la precede con una bolla sull’uscita, mentre se la porta presente non ha una bolla
sull’ingresso, disegnare la porta che la precede senza una bolla sull’uscita
