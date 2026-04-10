---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---

# Quando conviene usare una cache e quando no
---
L’efficacia della [[Cache]] dipende dalla dimensione della cache e dal tipo di lavoro che viene eseguito infatti lo stesso programma eseguito due volte potrebbe avere performance diverse. Detto questo prendendoli individualmente non riusciamo a predire la performance del programma mentre le iterazione tra le due determinano l efficacia della [[Cache]]

## Modello Working set

Un modello per capire come le cache sono utili è il working set, in questo modello possiamo contare come esista un punto in cui aumentare la dimensione della cache non aumenta l hit rate del cache e questo punto viene chiamato working-set

![[IMG - Quando conviene usare una cache quando no 1.jpeg]]

Nel tempo invece le prestazioni in termini di hit rate possono cambiare a seconda della fase del programma. In questi momento si intercambiano una fase di basso hit rate poi di lato e poi di uovo di basso, ogni parte bassa è l inizio di una nuova fase del programma mentre i momenti alti avvengono quando un programma è stato abbastanza tempo in quella fase da stabilizzare la cache.

![[IMG - Quando conviene usare una cache quando no 2.jpeg]]

Combinando i due grafi possiamo ottenere l impatto della dimensione del working set sulle performance del calcolatore. Notiamo che un programma che entra nella cache secondaria gira 4 volte più lento di uno che entra in quella primaria .

Si può provare a scrivere algoritmi che sfruttano la dimensione della cache per dividere il lavoro in moda da farle entrare nella cache primaria un esempio è il riordinamento di un array

![[IMG - Quando conviene usare una cache quando no 3.jpeg]]

## Zipf Model
In alcuni casi il modello migliore capire il comportamento delle cache è la zipf distribution siccome i fenomeni di popolarità  seguono approssimativamente questa curva

![[IMG - Quando conviene usare una cache quando no 4.jpeg]]

Nel caso di siti web la frequenza di vistai è inversamente proporzionale alla sua popolarità

I casi in cui il modello zipf funziona meglio e quando si verifica

- In caso in cui ci sono spesso nuovi dati e quelli vecchi cambiano
- Quando non esiste un working set ovvero non esiste uno specifico subset di dati che se cachato porta a benefici vistosi, in più aggiungere più cache porta a vantaggi sempre minori

![[IMG - Quando conviene usare una cache quando no 5.jpeg]]
