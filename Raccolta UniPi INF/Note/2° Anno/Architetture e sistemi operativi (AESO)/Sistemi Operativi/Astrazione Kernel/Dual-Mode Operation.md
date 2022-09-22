# Dual-Mode Operation

Il sistema operativo esegue  i processi  in due modalità:

- kernel-mode:  che ha accesso completo al hardwere
- user-mode: che privilegi limitati

[[Astrazione_Kernel_4.png]]

<aside>
💡 **Divisione sistema operativo**
non tutto il sistema operativo gira in kernel mode alcune parti come la gestione delle finestre girano come librerie sui i programmi che le utilizzano, quete sono in user-mode è permette di fare una netta divisione tra cio che ha bisogno di permessi privilegiati (kernel) e cio che non ne ha bisogno. questo amenta l affidabilita del sistema siccome un errore nel codice che gira in user-mode non puo provacare errori inaspettati in altri programmi non correlati

</aside>

Per realizzare la doppia modalità l hardware deve supportare almeno di queste tre componenti:

## Istruzioni Privilegiate

 tutte le operazioni potenzialmente “unsafe”  sono proibite in user-mode

## Protezione Memoria



tutte le operazioni al di furi della regione di memoria del processo valide sono proibite in user-mode questo viene realizato mediante l utilizzo di [[Memoria Virtuale]]

<aside>
💡 **Memory Mapped**
I Device di I\O sono mappati nella memoria quindi hanno un loro spazio di memoria dove leggere e scrivere dati. Il sistama di pretezione memoria impedisce anche che i programmi comunichino direttamente con queste zone senza passare per il kernel. Ciò significa che sarà il kernel a dover leggere e scrivere nella memoria dei programmi o dei device per permettere la comunicazione in modo controllato

</aside>

## Timer Interrupt

il kerne può prendere il controllo del processore periodicamente  indipendentemente da cosa sta eseguendo. questo grazie ad un timer hardwere  che puo scadere sia dopo un numero di millisecondo o dopo un numero di istruzioni. all ascadenza quello che gira sul processore passa dal essere il programma user mode al kernel che fara le suo operazionie ridara successivamente il controllo ad un programma user mode. resettare il timer è un istruzione privilegiata quindi solo il kernel puo farlo

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
