---
Course: "[[Architetture e sistemi operativi (AESO)]]"
topic: 
tags:
  - AESO
---


# Accesso al disco e performance
---


# Disk Access e Performance (Accesso al Disco e Prestazioni)
[[HardDisk Driver(HDD)|Disk Access]] 
I sistemi operativi inviano comandi al disco per leggere o scrivere settori consecutivi identificati da **LBAs (Logical Block Addresses)**. Il tempo di accesso a un disco è dato da:

**Tempo di accesso al disco = tempo di seek + tempo di rotazione + tempo di trasferimento**

## Seek (Ricerca della Traccia)
- Il disco muove il braccio sulla traccia desiderata, stabilizzandosi sulla posizione corretta.
- **Tempo minimo di seek**: 0.3–1.5 ms per spostarsi su una traccia adiacente.
- **Tempo massimo di seek**: oltre 10–20 ms per lo spostamento tra tracce più lontane.
- **Tempo medio di seek**: approssimativamente un terzo della distanza massima, ma spesso non rappresenta scenari reali poiché i dati sono spesso vicini tra loro.

## Rotazione
- Una volta sulla traccia corretta, il disco attende che il settore desiderato passi sotto la testina.
- **Latenza rotazionale**: metà del tempo di una rotazione completa (7.5–2 ms per dischi da 4200-15000 RPM).
- Alcuni dischi leggono in anticipo i settori per velocizzare i successivi accessi.

## Trasferimento dei Dati
- Dopo aver raggiunto il settore desiderato, i dati vengono trasferiti tra la testina e la memoria buffer del disco e poi alla memoria principale del sistema.
- **Tempo di trasferimento della superficie**: molto inferiore rispetto a seek e rotazione (tipicamente < 0.005 ms per settore).
- **Velocità di trasferimento**: varia da 60 MB/s (USB 2.0) fino a 2500 MB/s (Fibre Channel-20GFC).
- Nei trasferimenti multi-settore, il disco sovrappone le operazioni per ottimizzare il tempo complessivo.

## Declino del Cilindro
- Un cilindro è un insieme di tracce allineate verticalmente su più superfici.
- In passato, si usavano cilindri per ridurre i seek, ma oggi l’accesso tra tracce dello stesso cilindro ha un costo simile a quello tra tracce adiacenti, rendendo questa tecnica obsoleta.
