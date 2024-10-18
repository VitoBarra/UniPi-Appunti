---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# FAT Linked List
---


il [[File System]] FAT utilizza come struttura principale una [[Struttura dati - Lista linkata]]. è stato creato per [[Microsoft DOS]] ma oggi viene usata principalmente per dispostivi dove si preferisce mantenere una struttura semplice come ad pennette USB.

ha più versione una di questa è la versione FAT-32 che supporta volumi con $2^{28}$ blocchi e fili grandi al massimo $2^{32}-1$ byte quasi 4Gb

## Index Structure

l index structure di questo file system è detta file allocation table (FAT). questa è un array con ogni entry grande 32 bit. ogni entry mappa esattamente un blocco del volume e conterrà un puntatore al prossimo blocco del file oppure un ENDOFFILE. per raggiungere un file si deve partire dal file number preso dalla [[Directories dati nominati|directory]]  che sarà l indice del primo blocco e poi si dovrà seguire la catena di next per raggiungere tutto il file.

![[Untitled 45.png]]

## Tracciamento dello spazio libero

le FAT entry non utilizzate sono tutte a zero, quindi per trovare uno spazio libero il file system può cercare le entry a zero nel array

## Euristiche di località

solitamente questo file system ha un euristica molto semplice molto spesso è una [[next fit]]. ovvero il primo blocco che trova libero lo riempie questo frammenta velocemente il disco ma si può risolvere la cosa lanciando periodicamente uno strumento di deframmentazione

## Svantaggi

- pessima località. per via della sua euristica semplice porta a frammentazione
- random access scarso. per accedere ad uno specifico blocco bisogna seguire la catena di next fino a quel blocco
- metadati limitate e assenza di controllo d accesso. ha i metadati comuni ma non procura cose come metadati di sicurezza ad esempio il groupID e l owner.
- Non supporta hard link. i metadati sono nel file di directory e questo impedisce di avere una buona gestione degli hard link non potendo implementare buoni sistemi di [[Garbage Collector]]
- limitazioni sulla dimensione del volume e delle dimensione dei file. le entries della tabella di allocazione sono a 32 bit ma 4 sono riservati questo porta a poter  indicizzare solo $2^{28}$ blocchi  il che significa la dimensione massima del volume è $2^{28}\times block \ size \ in \ byte$  . mentre la dimensione dei file sono codificati con 32 bit il che rende il file più grande rappresentabile grande $2^{32}-1$ ovvero poco meno di 4Gb
- non supporta tecniche di affidabilità. non supporta gli update con transazioni. se il sistema operativo crasha durante una scrittura potrebbero esserci degli errori
