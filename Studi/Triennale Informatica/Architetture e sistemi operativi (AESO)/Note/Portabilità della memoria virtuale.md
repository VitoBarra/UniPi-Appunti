---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Portabilità
---

essendo i vari sistemi di [[Memoria Virtuale|memoria virtuale]] e quindi di traduzione degli indirizzi strutture solitamente hardware pongono il problema della portabilità del sistema operativo siccome questo deve poter girare sul maggior numero di dispositivi possibili.

Questo si ottiene con le seguenti strutture dati:

- **liste di oggetti di memoria**: sono segmenti logici che sono indipendenti dal implementazione della memoria del hardware che potrebbe essere non segmentata e servono al kernel per mantenere traccia di cosa rappresenta che tipo di dato. Degli esempi sono la regione del codice, [[Memory mapped file]], regione copy-on-Write ecc
- **Traduzione da indirizzi virtuali a fisici**: il kernel deve essere capace di capire se una pagina invalida è effettivamente invalida o è in uno dei casi in cui devono essere esegui te delle operazioni come copy-on-write o fill-on-reference
- **Traduzione da indirizzi fisici a virtuali**: la *core map* ovvero il sistema operativo deve tenere traccia di quali processi mappano quali aree di memoria in modo da poter aggiornare tutte le page table dei processi

Un approccio per realizzare una struttura dati interna al sistema operativo è utilizzare le hash table

Viene fatto l [[Struttura dati - Hash Table|hash]] del  il numero di pagina virtuale il risultato è direttamente il numero di pagina fisico l indirizzo raggiunto conterrà anche le informazioni d accesso, i dati necessari per la gestione delle collisioni e il numero di pagina virtuale il pid del processo che sta cercando di accedere a quella memoria. per andare a leggere effettivamente quella pagina fisica deve combaciare sia il numero di pagina virtuale salvata nel entry che il pid

![[Immagine_PNG.png]]

Le collisione si gestiscono con le solite tecniche  del [[Struttura dati - Hash Table]]

> [!info]
Perché non usiamo direttamente un hash table per
>![[3A5717D3-F044-4982-BD82-580994E0FDBF.jpeg]]

