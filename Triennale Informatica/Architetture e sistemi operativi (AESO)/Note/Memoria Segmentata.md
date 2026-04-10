---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags: AESO
---

# Memoria Segmentata
---
la memoria segmentata è un implementazione di [[Memoria Virtuale]]  e si tratta di un estensione del [[Base e Bound]] con più segmenti di memoria discontinui. salvando in hardware un array detto tabella dei segmenti  questa per ogni elemento avrà una coppia base e Bound più informazioni di permesso d accesso per una protezione della memoria più fine-grain

![[IMG - Memoria Segmentata 1.png]]

## Traduzione

la traduzione è simile a quella trovata per [[Base e Bound]]  ma indirizzo è formato da due parti:

- **segmento** : indica quale elemento del tabella guardare
- **offset**: quanto dovremmo aggiungere alla base per trovare l indirizzo fisico

quindi la [[Traduzione degli indirizzi virtuali|traduzione]]  sarà data da: SegmentTable\[segment\].base+offset

### Vantaggi

- **possibile espandere l Heap e lo Stack**: tutti i segmenti non dovendo essere necessariamente  contigui i segmenti possono essere messi in parti diversi della memoria indipendentemente e quindi possono crescere finche c è spazio contiguo nella regione in cui sono allocati. se non c è in alternativa il sistema operativo può spostare l intero segmento

 
> [!info] 
> 🛠 rendere più efficiente gestione della pulizia della memoria che si ottiene espandendo lo heap siccome lo si può fare con una pratica chiamata zero-on-reference essenzialmente al momento del espansione del heap viene sollevata un eccezione ed il kernel può occuparsi di azzerare la memoria che sta per essere allocata al Heap. questo si fa per motivi di sicurezza (in quella memoria potrebbero esserci scritti dati sensibili come password)

- **Condividere memoria tra processi**: se due processi devono condividere un segmento basterà aggiungerli entrambi nella tabella dei segmenti

    ![[IMG - Memoria Segmentata 2.png]]

- **supporto protezione memoria**: riesce a supportare una protezione della memoria esterna grazie al Bound e una protezione più fine-grane potendo gestire le regole d accesso a livello di segmento

### Problematiche

- **Frammentazione di memoria**: più processi sono sulla macchina più è difficile trovare abbastanza spazio per inserire nuovi segmenti o espanderli. essendo segmenti di dimensione variabile creano facilmente a gap nella memoria che con il tempo possono accumularsi e portare ad un elevata Frammentazione Esterna
