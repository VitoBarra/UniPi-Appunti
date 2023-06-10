
---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Mappe Di Karnaugh
---
le mappe di _Karnaugh_ servono a semplificare le [[Espressioni Booleane]] con un massimo di 4 variabili.

una mappa è una griglia circolare dove ogni spostamento di una riga o colonna corrisponde ad un cambiamento di una sola variabile la prima colonna è adiacente al ultima come la prima riga lo è con l ultima.

![[UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 13 1.png]]

regole per trovare l espressione prima partendo da un mappa di Karnaugh

Utilizzare il minor numero possibile di cerchi per includere tutti gli 1.
• Tutti i riquadri racchiusi in ciascun cerchio devono contenere 1.
• Ogni cerchio deve includere un numero di riquadri che sia una potenza di
due (cioè 1, 2 o 4 riquadri) in qualsiasi direzione.
• Ogni cerchio deve essere il più largo possibile.
• È possibile disegnare un cerchio che avvolga le estremità della mappa di
Karnaugh.
• Un 1 in una mappa di Karnaugh può essere cerchiato più di una volta, se
questa operazione permette di utilizzare un numero minore di cerchi.

