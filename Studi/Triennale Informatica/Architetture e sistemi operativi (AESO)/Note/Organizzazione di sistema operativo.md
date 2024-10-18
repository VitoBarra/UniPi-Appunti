---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Organizzazione di sistema operativo
---


There are many dependencies among the modules inside the operating
system, and there is often quite frequent interaction between these modules:

- Many parts of the operating system depend on synchronization primitives for
coordinating access to shared data structures with the kernel.
- The [[Memoria Virtuale]] system depends on low-level hardware support for address
translation, support that is specific to a particular processor architecture.
- Both the file system and the virtual memory system share a common pool of blocks of
physical memory. They also both depend on the disk device driver.
- The file system can depend on the network protocol stack if the disk is physically
located on a different machine.

This has led operating system designers to wrestle with a fundamental tradeoff: by
centralizing functionality in the kernel, performance is improved and it makes it easier to
arrange tight integration between kernel modules. However, the resulting systems are less
flexible, less easy to change, and less adaptive to user or application needs. We discuss
these tradeoffs by describing several options for the operating system architecture.

## Kernel Monolitico

kernel fatto in modo d avere buona parte dei moduli interni al kernel e con interazioni complesse tra di loro

![[Untitled 31.png]]

grafo dei moduli che richiamano funzioni in altri moduli tutti inseriti direttamente nel kernel per ragioni di performance

### layer di astrazione Hardware (HAL)

il layer d astrazione hardware è un interfaccia che permette al sistema operativo di non conoscere le implementazioni di funzioni prettamente hardware specifiche per ogni processore o macchina. queste vengono implementate in modo separato e poi linkate al interfaccia

### Driver per dispositivi dinamicamente installabili

sono software che gestiscono uno specifico dispositivo interfaccia o chipset aggiunto mentre il kernel sta già girando. Solitamente questi driver sono prodotti da chi produce l hardware e implementano un interfaccia standard supportata dal kernel. ogni volta che il [[Astrazione Kernel|kernel]] ha bisogno di comunicare con il dispositivo chiama quel interfaccia.

i driver possono essere eseguiti in kernel mode ma questo porta problemi di sicurezza e affidabilità.

 per risolvere questo problema ora i driver vengono per lo più scritti in user-mode.

per portare i driver legacy ad un livello di sicurezza simile si utilizzano [[macchine virtuali]]

![[Untitled 1 14 1.png]]

## MicroKernel

il microkernel prende un l approccio più modulare lasciando tutto quello che può non essere fatto nel kernel in user process. ad esempio il Windows manager può essere un server che gira in user space. al utente finale la cosa è trasparente siccome lui chiederà il servizio come se lo avesse il kernel ma sarà il kernel stesso a reindirizzare il lavoro al processo in user-space.

questo da un vantaggio sulla sicurezza e sul affidabilità ma  per via degli step in più da uno svantaggio sulle performance.
