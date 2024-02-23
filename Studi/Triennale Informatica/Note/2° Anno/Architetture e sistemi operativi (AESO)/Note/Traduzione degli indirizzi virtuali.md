---
Subject: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Traduzione degli indirizzi virtuali
---


la traduzione degli indirizzi è una pezzo di funzionalità che serve per tradurre gli indirizzi virtuali  con cui lavora il processo in indirizzi fisici che sono quelli con cui lavora la memoria fisica. questa funzionalità può essere realizzata sia con hardware che con software che con entrambi

![[Untitled 25 1.png]]

# Parametri

- **Protezione della memoria**: limitare i processi a poter scrivere solo nel proprio spazio di memoria cosi da evitare scritture erronee o malevole sulla memoria del resto della macchina oppure in zone di memoria dove potrebbe essere una cattiva idea scrivere come la zone del codice di quel programma
- **Condivisione di memoria**: condividere segmenti di memoria tra processi sia che questa sia la sezione codice di più istanze di un programma sia che sia una libreria comune o un file
- **Posizionamento flessibile nella memoria**: la capacita di inserire qualsiasi parte del programma in regioni casuali della memoria fisica, quindi rendendo indipendenti i programmi da dove vengono posizionati ad ogni avvio
- **Indirizzi sparsi**: avere programmi con più sezioni di memoria nella memoria fisica in modo che questa possa crescere indipendentemente dal resto del programma
- **Runtime lookup efficiency**: traduzione degli indirizzi efficienti siccome è necessaria una tradizione ad ogni istruzione e ad ogni load e store se queste fossero troppo lente  non sarebbe pratico realizzarle
- **Compact translation tables**: le dimensione delle strutture dati dovrebbero essere piccole rispetto alla memoria mappata
- **Portability**. ogni hardware fa scelte diverse per implementare la traduzione degli indirizzi quindi un sistema operativo portabile deve poter facilmente mappare le sue strutture hardwer-indipendent con quelle del hardwere.

[[Memoria Virtuale]]

## Address translation in linkers and loaders

Even without the kernel-user boundary, multiprogramming requires some form of address translation. On a
multiprogramming system, when a program is compiled, the compiler does not know which regions of
physical memory will be in use by other applications; it cannot control where in physical memory the
program will land. The machine instructions for a program contains both relative and absolute addresses;
relative addresses, such as to branch forward or backward a certain number of instructions, continue to work
regardless of where in memory the program is located. However, some instructions contain absolute
addresses, such as to load a global variable or to jump to the start of a procedure. These will stop working
unless the program is loaded into memory exactly where the compiler expects it to go.
Before hardware translation became commonplace, early operating systems dealt with this issue by using a
relocating loader for copying programs into memory. Once the operating system picked an empty region of
physical memory for the program, the loader would modify any instructions in the program that used an
absolute address. To simplify the implementation, there was a table at the beginning of the executable
image that listed all of the absolute addresses used in the program. In modern systems, this is called a
symbol table.
Today, we still have something similar. Complex programs often have multiple files, each of which can be
compiled independently and then linked together to form the executable image. When the compiler
generates the machine instructions for a single file, it cannot know where in the executable this particular file
will go. Instead, the compiler generates a symbol table at the beginning of each compiled file, indicating
which values will need to be modified when the individual files are assembled together.
Most commercial operating systems today support the option of dynamic linking, taking the notion of a
relocating loader one step further. With a dynamically linked library (DLL), a library is linked into a running
program on demand, when the program first calls into the library. We will explain in a bit how the code for a
DLL can be shared between multiple different processes, but the linking procedure is straightforward. A table
of valid entry points into the DLL is kept by the compiler; the calling program indirects through this table to
reach the library routine.

- **Indirizzi fisici di memoria**: cioè il sistema deve cambiare le locazioni di memoria indicate dal programma ricalcolando le tutte a partire dal indirizzo di inizio scelto per quella particolare  istanza del programma in esecuzione

