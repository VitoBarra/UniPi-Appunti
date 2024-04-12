---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Directories dati nominati
---


una directory è un file che da una mappatura $nome \rightarrow n\ file$

![[Untitled 46.png]]

questa definizione ci permette di organizzare le directory in modo gerarchico facendo puntare una entry di una directory ad un altra directory



![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 21.png]]

per iniziare questa catena si parte da una directory ben conosciuta denominata “root” e indicata con “/” di solito questa ha numero di file 2.

## Implementazione interna

inizialmente l implementazione delle directory era fatta in modo lineare per accomodare un caso comune al tempo ovvio pochi file per directory. per ottenere questo si utilizzava un implementazione con una [[Struttura dati - Lista linkata]]

![[Untitled 2 8 1.png]]

questa implementazione presenta problemi di performance quando i file per directory iniziano ad essere tanti. quindi si preferisce una struttura ad albero

![[Untitled 3 6 1.png]]

questa implementazione è realizzata con un [[Struttura dati - B-Tree]] e utilizza l hash del nome del file da raggiungere e poi lo usa internamente per scendere nel albero.
ogni nodo contiene una lista di coppie hash e pointer (sotto forma di offset dal inizio del file) al prossimo nodo a al file se il nodo è una foglia

![[Untitled 4 3 1.png]]

fisicamente nel file al inizio sono messi tutte le coppie file $nome \rightarrow n\ file$ e dopo queste c è il nodo root del albero che inizia in un offset conosciuto a priori ad esempio tenuto in BTREE_ROOT_PTR

## Soft e Hard link

soft e hard link sono modi che offre il file system per dare più nomi allo stesso file.. permettere questo significa avere più path che portano allo stesso file nel caso degli hard link e avere path che mappano ad altri path nel caso dei soft link



![[UniPi-Appunti/Studi/Triennale Informatica/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 5 1 1.png]]

 implementare questo rende la struttura delle directory un [[Struttura dati - DAG]]

![[Untitled 6 1 1.png]]

in caso di hard link un file deve essere cancellato solo se tutti i path che lo mappano vengono cancellati quindi per implementare un sistema corretto di [[Garbage Collector]] dei file si utilizza [[Reference Counting]].

>[!info]
 per una gestione più efficiente del reference counting i metadata dei file sono scritti in un header nel file e non nella directory, altrimenti si sarebbe dovuta gestire l aggiornamento di tutti gli hard link e quindi la loro locazione
