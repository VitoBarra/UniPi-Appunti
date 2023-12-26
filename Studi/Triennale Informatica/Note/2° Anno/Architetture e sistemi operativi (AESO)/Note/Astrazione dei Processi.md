---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Astrazione dei Processi
---
Il kernel per eseguire un processo che è un istanza di un programma alloca in memoria lo stack e lo heap del dato programma e per farlo girare  salta alla sua prima istruzione.

Il [[Sistemi Operativi|Sistema operativo]] tiene traccia  dei processi  con una struttura dati chiamata PCB ovvero Process Control Block dove sono presenti informazioni tipo:

- dove è L immagine del eseguibile è locato sul disco
- con che privilegi è stato avviato il processo
- e cosi via

>[!info] #### Processi e Thread
>
>- I processi sono una sequenza di istruzioni  in stanze di un programma
>- I [[Astrazione Thread|Thread]] sono multiple sequenze di istruzioni associate ad un processo che lavorano in modo concorrente o parallelo negli stessi confini di protezione
