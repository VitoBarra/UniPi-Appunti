---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Flash storage access and performance
---
per scrivere su una [[SolidState Driver (SSD)|memori flash]] bisogna cancellare un erasure block mettendoli tutti ad uno e riscriverla,gli erasure block sono grandi 128kb -512 kb , la scrittura e la lettuttura possono essere fatta per pagina, una pagina è tipiacamente 2048-4096 byte

Durability. Normally, flash memory can retain its state for months or years without power.
However, over time the high current loads from flashing and writing memory causes the
circuits to degrade. Eventually, after a few thousand to a few million program-erase cycles
(depending on the type of flash), a given cell may wear out and no longer reliably store a
bit.

In addition, reading a flash memory cell a large number of times can cause the surrounding
cells’ charges to be disturbed. A read disturb error can occur if a location in flash memory
is read to many times without the surrounding memory being written.
To improve durability in the face of wear from writes and disturbs from reads, flash devices
make use of a number of techniques:
Error correcting codes. Each page has some extra bytes that are used for error
correcting codes to protect against bit errors in the page.
Bad page and bad erasure block management. If a page or erasure block has a
manufacturing defect or wears out, firmware on the device marks it as bad and stops
storing data on it.
