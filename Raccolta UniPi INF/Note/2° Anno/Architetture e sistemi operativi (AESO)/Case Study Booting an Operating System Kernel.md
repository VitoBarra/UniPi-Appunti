---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Case Study Booting an Operating System Kernel
---
per avviare un sistema operativo si una un Boot [[ROM]] che è una memoria che cambia molto raramente e che contiene un programma che viene eseguito al avvio della macchina. questo si chiama BIOS e caricare un numero fisso di bit da una posizione fissa del disco. questo serve per caricare il boot loader del sistema operativo. il bootloader caricherà il kernel che avvierà poi il primo processo solitamente il loggin page.

questa separazione BIOS sistema operativo è comoda siccome il sistema operativo va aggiornato spesso e farlo su una [[ROM]] potrebbe portare a corrompere del tutto la macchina in caso di imprevisti durante l aggiornamento

![[Untitled 35.png]]

molti BIOS moderno ora controllano anche che il bootlaoder non sia corrotto utilizzando sistemi crittografici come la firma crittografica. quindi utilizzando una chiave privata validata con una chiava pubblica per controllare se l file è valido
