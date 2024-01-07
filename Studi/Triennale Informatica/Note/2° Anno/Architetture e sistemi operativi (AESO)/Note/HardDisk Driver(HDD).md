---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags:
  - AESO
Parent MOC: "[[Architetture e sistemi operativi (AESO)]]"
---
# HardDisk Driver(HDD)
---
Dispositivi per il mantenimento persistente di dati. Questi dischi sono formati da più dischi inpilati su di uno spindle che puo far ruotare i dischi. I dati sono salvati su ogni faccia dei deschi e sono letti e scritti da delle testine attaccate a dei bracci attacchati anche essi ad un palo con un motore alla fine detto arm assembly. C è un braccio per ogni superficie e una testina puo leggere almeno un settore alla volta.

 I settori sono tipichimante grandi 512 byte. I dischi sono organizzati a settori perché questi comprendano dei bit per il controllo dei gli errori. Questo permette di aumentare la banda di lavoro. Un un cerchi di settori si chiama track

![[6E45A0F5-B760-4B92-BFE6-D4D3BFAAF40D.jpeg]]

![[AC0332EB-0DF8-4984-B7E6-0B3DE7BF7426.jpeg]]

To maximize sequential access speed, logical sector zero on each track is staggered from sector zero on the previous track by an amount corresponding to time it takes the disk to move the head from one track to another or to switch from the head on one surface to the head on another one. This staggering is called track skewing.

To increase storage density and disk capacity, disk manufacturers make tracks and sectors as thin and small as possible. If there are imperfections in a sector, then that sector may be unable to reliably store data. Manufacturers therefore include spare sectors distributed across each surface. The disk firmware or the file system’s low-level formatting can then use sector sparing to remap sectors to use spare sectors instead of faulty sectors. Slip sparing helps retain good sequential access performance by remapping all sectors from the bad sector to the next spare, advancing each logical sector in that range by one physical sector on disk.

Disk drives often include a few MB of buffer memory, memory that the disk’s controller uses to buffer data being read from or written to the disk, for track buffering, and for write acceleration.

Track buffering improves performance by storing sectors that have been read by the disk head but have not yet been requested by the operating system. In particular, when a disk head moves to a track, it may have to wait for the sector it needs to access to rotate under the disk head. While the disk is waiting, it reads unrequested sectors to its rack buffer so that if the operating system requests those sectors later, they can be returned immediately.

Write acceleration stores data to be written to disk in the disk’s buffer memory and acknowledges the writes to the operating system before the data is actually written to the platter; the disk firmware flushes the writes from the track buffer to the platter at some later time. This technique can significantly increase the apparent speed of the disk, but it carries risks — if power is lost before buffered data is safely stored, then data might be lost.

Server drives implementing the SCSI or Fibre Channel interfaces and increasing numbers of commodity drives with the Serial ATA (SATA) interface implement a safer form of write acceleration with tagged command queueing (TCQ) (also called native command queueing (NCQ) for SATA drives.) TCQ allows an operating system to issue multiple concurrent requests to the disk and for the disk to process those requests out of order to optimize scheduling, and it can be configured to only acknowledge write requests when the blocks are safely on the platter.


