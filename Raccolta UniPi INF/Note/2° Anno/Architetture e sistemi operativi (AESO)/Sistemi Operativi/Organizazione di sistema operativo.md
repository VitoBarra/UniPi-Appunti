# Organizazione di sistema operativo

There are many dependencies among the modules inside the operating
system, and there is often quite frequent interaction between these modules:

- Many parts of the operating system depend on synchronization primitives for
coordinating access to shared data structures with the kernel.
- The virtual memory system depends on low-level hardware support for address
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

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Sistemi Operativi/Organizazione di sistema operativo/Untitled.png]]

grafo dei moduli che richiamano funzioni in altri moduli tutti inseriti direttametne nel kernel per ragioni di performance

### layer di astrazione Hardware (HAL)

il layer d astrazione hardware è un interfaccia che permette al sistema operativo di non conoscere le implementazioni di funzioni prattamente hardwere specifiche per ogni processore o macchina. queste vengono implementate in modo separato e poi linkate al interfaccia

### Driver per dispositivi dinamicamente installabili

sono softwere che gestiscono uno specifico dispositivo interfaccia o chipset aggiunto mentre il kernel sta gia girando. Solitamente questi driver sono prodotti da chi produce l hardwere e implementano un interfaccia standard supportata dal kernel. ogni volta che il chernel ha bisogno di comunicare con il dispositivo chiama quel interfaccia.

i driver posono essere eseguiti in kernel mode ma questo porta problemi di sicurezza e affidabilita.

 per risolvere questo problema ora i drivere vengono per lo piu scritti in user-mode.

per portare i driver legacy ad un livello di sicurezza simile si utilizzano macchine vertuali

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Sistemi Operativi/Organizazione di sistema operativo/Untitled 1.png]]

## MicroKernel

il microkernel prende un l aproccio piu modulare lasciando tutto quello che puo non essere fatto nel kernel in user process. ad esempio il Widows manager puo essere un servere che gira in user space. al utente finale la cosa è trasparente siccome lui chidera il servizio come se lo avesse il kernel ma sara il kernel stesso a reindirizzare il lavoro al processo in user-space.

questo da un vantaggio sulla sicurezza e sull affidabilita ma  per via degli step in piu da uno svantaggio sulle performance.

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
