# Memoria Paginata

la memoria pagina la memoria viene allocata in pezzi dimensione fissa questi pezzi chiamati page frames questo permette di avere le varie parti di un processo sparse e divise nella memoria cosi che al processore sembrerà contigua mentre in memoria fisica non lo sarà

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 18.png]]

## Traduzione

in indirizzo virtuale è fatto da due componenti:

- **Page#**: ovvero il numero di pagina da prendere nella page table
- **offset**: ovvero il numero da aggiungere alla base della pagina scelta

[[Untitled 1 1 1.png]]

### Vantaggi

- **possibile espandere l Heap e lo Stack**: le varie pagine possono di heap e stack possono essere discontinue quindi per espanderli basta allocare una nuova pagine in zone arbitrarie libere della memoria questa viene mappata con una bitmap che indica se una pagina è libera o piena quindi per allocare una nuova pagina basta cercare nella bitmap un bit che indichi che la pagina è libera
- **supporto protezione memoria**: la protezione di memoria si ottiene con un bit di permessi sulla singola pagina quindi è supportata solo fine-grane
- **Condividere memoria tra processi**: se due processi devono condividere delle pagine di memoria serve una struttura dati che mantenga il numero dei link a quel page frame questa è chiamata Core Map
- **Ottimizzazioni possibili**: si può avviare un programma mentre alcune pagine non sono ancora state caricate in memoria se queste vengono richiamate si solleverà un eccezione che caricherà le pagine mancanti richieste con page demanding

### Problematiche

- librerie e processi si aspettano di lavorare con memorie continue
- difficile gestione di programmi multithread perché ogni thread ha bisogno di un suo stack
- grande overhead con con spazio degli indirizzi virtuale sparso
- Internal fragmentation se le pagine sono troppo grandi
- grande spreco di spazio se le pagine sono troppo grandi e quindi parte non sono usate
- grande spreco di spazio se le pagine sono piccole siccome la tabella degli indirizzi deve essere più grande
