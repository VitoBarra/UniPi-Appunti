---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# NTFS Flexible Tree With Extents
---


The Microsoft New Technology File System (NTFS), released in 1993, improved on
[[FAT Linked List|Microsoft’s FAT]] file system with many new features including new index structures to
improve performance, more flexible file metadata, improved security, and improved
reliability.

## Index Structure

questo [[File System]] utilizza un un [[array]] chiamato master file table (MFT) ogni entry mantiene degli attributi di un file. questi attributi sono la radice del albero dinamico e sono :

-__standard information__: permessi d accesso, ultima modifica, dimensione totale ecc
-__file name__ : ogni file può avere più nomi quindi qui potrebbero esserci più nomi
- __dati__: i dati del file fisico salvati in extents ovvero sequenze contigue di lunghezza arbitraria

ogni attributo può essere residente o non residente. se è residente allora è tutto contenuto nel entry altrimenti l entry contiene dei puntatori a delle extents esterne che mantengono quel attributo

![[Untitled 43.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 1 19.png]]

in caso gli attributi crescano molto e non riescano ad entrare in un entry del MFT il file system può utilizzare più entry per lo stesso file. per fare questo viene aggiunto un attributo

- _attribut list_: ovvero una lista di puntatoti ad altri attributi presenti sia nella stessa entry che in altre

![[Untitled 2 6 1.png]]

ci sono varie situazioni che cambiano il comportamento del NTFS ovvero

- file piccoli : tutto entra in un entry
- file normali: sono gli attributi dei dati sono non residenti
- file grandi/molta frammentazione: attribute list che indica dove trovare i dati su più entry della MFT
- file giganteschi/ frammentazione estrema: atribute list non residente e questa punta a più blocchi dati in più MFT con dati non residenti

![[Untitled 3 4 1.png]]

## Tracciamento dello spazio libero

il tracciamento dei blocchi libero è realizzato tramite bitmap salvata come file stesso in una posizione ben conosciuta, cosi come la master file table (MFT) stessa

## Euristiche di località

utilizza un euristica Best Fit ovvero piazza i nuovi blocchi nella regione libera piu piccola possibile che li contiene tutti.

 per evitare la frammentazione del MFT il file system riserva la parte iniziale del disco per poter fare spazio alla MFT che cresce

ha un tool di deframmentazione
