---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Dual-Mode Operation
---
Il sistema operativo esegue i processi  in due modalità:

- kernel-mode:  che ha accesso completo al hardware
- user-mode: che privilegi limitati

![[Astrazione_Kernel_4.png]]
> [!info]
> le due modalità sono utili sono se esistono metodi sicuri per passare da un modalità al altra: [[Tipi di cambio di modalità]]

>[!info] **Divisione sistema operativo**
non tutto il sistema operativo gira in kernel mode alcune parti come la gestione delle finestre girano come librerie sui i programmi che le utilizzano, queste sono in user-mode è permette di fare una netta divisione tra ciò che ha bisogno di permessi privilegiati (kernel) e ciò che non ne ha bisogno. questo aumenta l affidabilità del sistema siccome un errore nel codice che gira in user-mode non può provocare errori inaspettati in altri programmi non correlati

Per realizzare la doppia modalità l hardware deve supportare almeno di queste tre componenti:

## Istruzioni Privilegiate

 tutte le operazioni potenzialmente “unsafe”  sono proibite in user-mode

## Protezione Memoria

tutte le operazioni al di furi della regione di memoria del processo valide sono proibite in user-mode questo viene realizzato mediante l utilizzo di [[Memoria Virtuale]]


>[!info]  **Memory Mapped**
I Device di I\O sono mappati nella memoria quindi hanno un loro spazio di memoria dove leggere e scrivere dati. Il sistema di protezione memoria impedisce anche che i programmi comunichino direttamente con queste zone senza passare per il kernel. Ciò significa che sarà il kernel a dover leggere e scrivere nella memoria dei programmi o dei device per permettere la comunicazione in modo controllato

## Timer Interrupt

il kernel può prendere il controllo del processore periodicamente  indipendentemente da cosa sta eseguendo. questo grazie ad un timer hardware  che può scadere sia dopo un numero di millisecondo o dopo un numero di istruzioni. al scadenza quello che gira sul processore passa dal essere il programma user mode al kernel che farà le suo operazioni ridarà successivamente il controllo ad un programma user mode. resettare il timer è un istruzione privilegiata quindi solo il kernel può farlo
