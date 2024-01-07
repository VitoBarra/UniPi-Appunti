---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags:
  - AESO
Parent MOC: "[[Architetture e sistemi operativi (AESO)]]"
---
# Memoria Paginata
---
La _memoria paginata_ è un implementazione della [[Memoria Virtuale]]. 
la _memoria fisica_ viene allocata in pezzi dimensione fissa questi pezzi chiamati __page frames__ questo permette di avere le varie parti di un processo sparse e divise in zone diverse della memoria fisica ma la processo la memoria apparirà contigua

![[Studi/Triennale Informatica/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 18.png]]

## Traduzione

l indirizzo virtuale è fatto da due componenti:

- **Page#**: ovvero il numero di pagina da prendere nella page table
- **offset**: ovvero il numero da aggiungere alla base della pagina scelta

![[Untitled 1 1 1 1.png]]
quindi la [[Traduzione degli indirizzi virtuali|traduzione]] sarà data da: PageTable\[Page#\]+Offset

#### Vantaggi
- **possibile espandere l Heap e lo Stack**: le varie pagine possono di heap e stack possono essere discontinue quindi per espanderli basta allocare una nuova pagine in zone arbitrarie libere della memoria questa viene mappata con una bitmap che indica se una pagina è libera o piena quindi per allocare una nuova pagina basta cercare nella bitmap un bit che indichi che la pagina è libera
- **supporto protezione memoria**: la protezione di memoria si ottiene con un bit di permessi sulla singola pagina quindi è supportata solo fine-grane
- **Condividere memoria tra processi**: se due processi devono condividere delle pagine di memoria serve una struttura dati che mantenga il numero dei link a quel page frame questa è chiamata Core Map
- **Ottimizzazioni possibili**: si può avviare un programma mentre alcune pagine non sono ancora state caricate in memoria se queste vengono richiamate si solleverà un eccezione che caricherà le pagine mancanti richieste con page demanding

#### Problematiche
- librerie e processi si aspettano di lavorare con memorie continue
- difficile gestione di programmi multithreading perché ogni thread ha bisogno di un suo stack
- grande overhead con con spazio degli indirizzi virtuale sparso
- Internal fragmentation se le pagine sono troppo grandi
- grande spreco di spazio se le pagine sono troppo grandi e quindi parte non sono usate
- grande spreco di spazio se le pagine sono piccole siccome la tabella degli indirizzi deve essere più grande
