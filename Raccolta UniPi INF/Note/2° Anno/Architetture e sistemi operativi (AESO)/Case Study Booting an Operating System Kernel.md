# Case Study: Booting an Operating System Kernel

per avviare un sistema operativo si unsa un Boot ROM che è una memoria che cambia molto raramente e che contiene un programma che viene eseguito al avvio della macchina. questo si chiama BIOS e caricare un numero fisso di bit da una posizione fissa del disco. questo serve per caricare il boot loader del sitema operativo. il bootloader carichera il kernel che avviera poi il primo processo solitamente il loggin page.

questa separazione BIOS sistema operativo è commoda siccome il sistema operativo va aggiornato spesso e farlo su una ROM potrebbe portare a corrompere del tutto la macchina in caso di imprevisti durante l aggiornameto

[[Untitled 35.png]]

molti BIOS moderno ora controllano anche che il bootlaoder non sia corrotto utilizando sistemi crittografici come la firma crittografica. quindi utilizzando una chiave privata validata con una chiava publica per controllare se l file è valido

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
