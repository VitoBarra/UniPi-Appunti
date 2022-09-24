# NTFS: Flexible Tree With Extents

The Microsoft New Technology File System (NTFS), released in 1993, improved on
Microsoft’s FAT file system with many new features including new index structures to
improve performance, more flexible file metadata, improved security, and improved
reliability.

## Index Structure

questo file system utilizza un un array chiamato master file table (MFT) ogni entry mantiene degli attributi di un file. questi attributi sono la radice del albero dinamico e sono :

- standard informatin: permessi d accesso, ultima modifica, dimensione totale ecc
- file name : ogni file può avere più nomi quindi qui potrebbero esserci più nomi
- dati: i dati del file fisico salvati in extend ovvero sequenze contigue di lunghezza arbitraria

ogni attributo può essere residente o non residente. se è residente allora è tutto contenuto nel entry altrimenti l entry contiene dei puntatori a delle extent esterne che mantengono quel attributo

[[Untitled 43.png]]

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 19.png]]

in caso gli atributi crescano molto e non riescano ad entrare in un entry del MFT il file system puo utilizzare piu entry per lo stesso file. per fare questo viene aggiunto un attributo

- attribut list: ovvero una lista di puntatoti ad altri atributi presenti sia nella stessa entry che in altre

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 2 6.png]]

ci sono varie situazioni che cambiano il comportamento del NTFS ovvero

- file piccoli : tutto entra in un entry
- file normali: sono gli atributi dei dati sono non residenti
- file grandi/molta frammentazione: attribute list che indica dove trovare i dati su piu entry dek MFT
- file giganteschi/ frammentazione estrema: atribute list non residente e questa punta a piu blocchi dati in piu MFT con dati non residenti

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 3 4.png]]

## Tracciamento dello spazio libero

il tracciamento dei blocchi libero è realizato tramite bitmap  salvata come file stesso in una posizione ben conosciuta, cosi come la MFT stessa

## Euristiche di località

utilizza un euristica Best Fit ovvero piazza i nuovi blocchi nella regione libera piu piccola possibile che li contiene tutti.

 per evitare la frammentazione del MFT il file system riserva la parte iniziale del disco per poter fare spazio alla MFT che cresce

ha un tool di deframmentazione
