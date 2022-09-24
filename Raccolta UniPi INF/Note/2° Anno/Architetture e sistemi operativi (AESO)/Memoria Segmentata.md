# Memoria Segmentata

la memoria segmentata si tratta di un stensione del [[Base e Bound]] con piu segmenti di memoria discontinui salvando in hardwere un array detto tabella dei segmenti  questa per ogni elemento avra una coppia base e bound piu informazioni di permesso d accesso per una protezione della memoria piu fine-grain

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 3 3.png]]

## Traduzione

la traduzione è simile a quella trovata per [[Base e Bound]]  ma indirizzo è formato da due parti:

- **segmento** : indica quale elemento del tabella guardare
- **offset**: quanto dovremmo aggiungere alla base per trovare l indirizzo fisico

quindi l indirizzo sarà SegmentTable[segment].base+offset

### Vantaggi

- **possibile espandere l Heap e lo Stack**: tutti i segmenti non dovendo essere necessariamente  contigui i segmenti possono essere messi in parti diversi della memoria indipendentemente e quindi possono crescere finche c è spazio contiguo nella regione in cui sono allocati. se non c è in alternativa il sistema operativo puo spostare l intero segmento

    <aside>
    🛠 rendere più efficiente gestione della pulizia della memoria che si ottiene espandendo lo heap siccome lo si può fare con una pratica chiamata zero-on-reference essenzialmente al momento del espansione del heap viene sollevata un eccezione ed il kernel può occuparsi di azzerare la memoria che sta per essere allocata al Heap. questo si fa per motivi di sicurezza (in quella memoria potrebbero esserci scritti dati sensibili come password)

    </aside>

- **Condividere memoria tra processi**: se due processi devono condividere un segmento basterà aggiungerli entrambi nella tabella dei segmenti

    [[Untitled 1 2 1.png]]

- **supporto protezione memoria**: riesce a supportare una protezione della memoria esterna grazie al bound e una protezione più fine-grane potendo gestire le regole d accesso a livello di segmento

### Problematiche

- **Frammentazione di memoria**: più processi sono sulla macchina più è difficile trovare abbastanza spazio per inserire nuovi segmenti o espanderli. essendo segmenti di dimensione variabile creano facilmente a gap nella memoria che con il tempo possono accumularsi e portare ad un elevata Frammentazione Esterna
