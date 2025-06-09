---
Course: "[[Information Retrieval (IR)]]"
tags:
  - IR
topic: nota
---
# Information Retrieval - Concetti generali
---
Con il termine **Information retrieval** si intende il processo per ottenere informazioni rilevanti da un grande insieme di dati non strutturati, come documenti, pagine web or contenuti multimediali, partendo da una query dell'utente.

Questo processo comprende la **ricerca** e l'**[[Indexing a document|indexing]]** dei dati per trovare il pezzo di informazione con **rilevanza** maggiore. 

si usa specialmente nei [[Search engine]].

### Componenti principali

I componenti chiave dell'information retrieval sono:
- [[Document representation]]: i sistemi di IR processano e rappresentano i dati in strutture per consentire una ricerca **efficiente**.  Questo processo comprende tokenizzazione, parsing e [[Indexing a document|indexing]]
- [[Query processing]]: Serve per processare la query inserita dall'utente e farla usare correttamente al sistema. Per far ciò la query viene spezzettata in keywords o in elementi semantici per essere poi confrontata con gli elementi dei documenti indicizzati.
- [[Weighting models-Ranking and relevance|Ranking e rilevanza]]: La parte principale di un sistema di IR è determinare quali documenti sono rilevanti e quali no. Per fare ciò usiamo algoritmi di ranking che danno un punteggio alla rilevanza di un documento in base a fattori come la presenza e la frequenza di keywords, matching semantico o casi d'uso.
- [[Evaluation metrics]]: Come metriche per misurare le performance di un sistema di IR si usano la **precision**, ossia quanto è rilevante il risultato fornito, e la **recall**, che indica quanti documenti rilevanti il sistema è stato in grado di fornire.

### Obiettivi sistemi IR
I due principali obiettivi di un sistema di information retrieval sono l'***Effectiveness*** e l'***Efficiency***.

L'***effectiveness*** (Efficacia) si riferisce a quanto bene un sistema IR è in grado di estrarre i documenti rilevanti rispetto ad una query. Questa si misura con le [[Evaluation metrics|evaluation metrics]] e la soddisfazione dell'utente. Il focus è nell'estrazione di risultati accurati e di alta qualità che incontrano le necessità dell'utente.

L'***efficiency*** (efficienza) include l'abilità del sistema di recuperare dei risultati velocemente e gestire una grande scala di documenti in tempi moderati. ci si occupa quindi del tempo di risposta, delle risorse utilizzate e della scalabilità del sistema, assicurandoci che l'utente riceva i risultati senza grossi ritardi , anche all'aumentare dei dati.

### Sfide
Tra le sfide dei sistemi di IR ci sono principalmente:
- Il linguaggio naturale: Il quale è complesso per la presenza di sinonimi, omonimi, sintassi e semantica delle frasi. La gestione del linguaggio influisce su quanto bene un sistema possa recuperare dati rilevanti. Si usano quindi tecniche di [[Natural Language Processing]].
- La rappresentazione dei documenti : che può cambiare in base al [[Retrieval models||retrieval model]] utilizzato. Il come vengono rappresentati i documenti influisce su quanto bene il sistema possa matchare query e documenti.