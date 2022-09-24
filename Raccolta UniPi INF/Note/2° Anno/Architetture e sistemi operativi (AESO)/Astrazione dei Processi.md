# Astrazione dei Processi

Il kernel per eseguire un processo che è un instanza di un programma alloca in memoria lo stock e lo heap del dato programma e per farlo girare  salta alla sua prima istruzione.

Il sistema operativo tiene traccia  dei processi  con una struttura dati chiamata PCB ovvero Process Control Block dove sono presenti informazioni tipo:

- dove è L immagine del eseguibile è locato sul disco
- con che privilegi è stato avviato il processo
- e cosi via



## Processi e Thread

- I processi sono una sequenza di istruzioni  in stanze di un programma
- I Thread sono multiple sequenze di istruzioni associate ad un processo che lavorano in modo concorrente o parallelo negli stessi confini di protezione

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
