# Directories: dati nominati

una directory è un file che da una mappatura $nome \rightarrow n\ file$

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled.png]]

questa definizione ci permette di organizare le directory in modo gerarchico facendo puntare una entry di una directory ad un altra directory



[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 1.png]]

per iniziare questa catena si parte da una directory ben conosciuta denominata “root” e indicata con “/” di solito questa ha numero di file 2.

## Implementazione interna

inizialmente l implementazione delle directory era fatta in modo lineare per accomodare un caso comune al tempo ovvio pochi file per directory. per ottenere questo si utilizzava un implementazione con una [liked list](../../../../1%C2%B0%20Anno%2015c52d0d476a4f1b893180fa95d41e07/Progamazione%20Algoritmica%20(ProgAlg)%20180740b2754b45b88e5ff26e1498115b/Strutture%20Dati%20f2ac0953e0294c01b6e04a7b78549686/Lista%20linkata%20cc33e6de05a14f1a84dbdce541bb8a36.md)

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 2.png]]

questa implementazione presenta problemi di performance quando i file per directory iniziano ad essere tanti. quindi si preferisce una struttura ad albero

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 3.png]]

questa implementazione è realizzata con un [B-tree](../../../../1%C2%B0%20Anno%2015c52d0d476a4f1b893180fa95d41e07/Progamazione%20Algoritmica%20(ProgAlg)%20180740b2754b45b88e5ff26e1498115b/Strutture%20Dati%20f2ac0953e0294c01b6e04a7b78549686/Albero%20f444155c4bb3482489341ef626172c62/B-Tree%20616df4d6d80847728b33e0b4bb77a944.md) e utilizza l hash del nome del file da ragiungere e poi lo usa internamente per scendere nel albero.
ogni nodo contiene una lista di coppie hash e pointer (sotto forma di offset dal inizio del file) al prossimo nodo a al file se il nodo è una foglia

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 4.png]]

fisicamente nel file al inizio sono messi tutte le coppie file $nome \rightarrow n\ file$ e dopo queste c è il nodo root del albero che inizia in un offset conosciuto a priori ad esempio tenuto in BTREE_ROOT_PTR

## Soft e Hard link

soft e hard link sono modi che offre il file system per dare più nomi allo stesso file.. permettere questo significa avere piu path che portano allo stesso file nel caso degli hard link e avere path che mappano ad altry path nel caso dei soft link



[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 5.png]]

 implementare questo rende la struttura delle directory un [DAG](../../../../1%C2%B0%20Anno%2015c52d0d476a4f1b893180fa95d41e07/Progamazione%20Algoritmica%20(ProgAlg)%20180740b2754b45b88e5ff26e1498115b/Strutture%20Dati%20f2ac0953e0294c01b6e04a7b78549686/Albero%20f444155c4bb3482489341ef626172c62/DAG%20295b4173a0e9472e8f4dd6efe07ce60d.md)

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/File System/Implementazione File System/Directories dati nominati/Untitled 6.png]]

in caso di hard link un file deve essere cancellato solo se tutti i path che lo mappano vengono cancellati quindi per implementare un sistema corretto di [garbage collector](../../../Paradigmi%20Di%20Programazione%20(PDP)%202ab8054c5494467d9ec9c760663a8888/Gestore%20della%20memoria%208a007bcc9a164fd69367acd21c791c63/Garbage%20Collector%204bfc1c6a3bea40308d2bfdb2ff143b86.md) dei file si utilizza [reference counting](../../../Paradigmi%20Di%20Programazione%20(PDP)%202ab8054c5494467d9ec9c760663a8888/Gestore%20della%20memoria%208a007bcc9a164fd69367acd21c791c63/Garbage%20Collector%204bfc1c6a3bea40308d2bfdb2ff143b86/Reference%20Counting%20ba2803eb6acf43169187490a71f3809b.md).

<aside>
💡 per una gestione più efficiente del reference counting i metadata dei file sono scritti in un header nel file e non nella directory, altrimenti si sarebbe dovuta gestire l aggiornamento di tutti gli hard link e quindi la loro locazione

</aside>
