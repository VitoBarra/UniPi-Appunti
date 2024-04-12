---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Stream IO
---
Gestione Del IO, con Java.IO basato sul concetto di stream che sono 
- mono-direzionale  (ovvero _InputStream_ e _OutStream_ sono separati)
- Accesso [[Coda struttura dati|FIFO]] 
- di uso generale
- Adatto a trasferire byte e caratteri
- Bloccante (attende sulla I-O se non ci sono Dati)


gli stream di input output son astrazioni del linguaggio su i dispositivi di ingresso uscita, comunicano tramite Row Byte

![[UniPi-Appunti/Studi/Triennale Informatica/3° Anno/Reti - lab 3/Media/Untitled 3.png]]



### motologia:
lo stream di byte di base è pensato per essere estendibile Jave da gia di default delle implementazionipiu puntuali di _InputStream_ e _OutPutStream_
![[Pasted image 20220925224212.png]]
Sono pensati per essere usati Concatenando più stream si può lavorare a livello più altro rispetto al semplice leggere byte ad esempio con il ==dataInputStream== si può leggere direttamente interi invece che byte
![[Pasted image 20220925224126.png]]


Con il _FileIO Stream_
- Per legge da uno stream bisogna usare il metodo _read_
- Per scrivere byte si usa il medito _Write_

utilizzare BufferedIOStream che estendono FilterIOStream da vantaggio in termini di prestazioni 

altri Stream come i DataIOStream che trasformano una sequenza di byte Row in dei dati a più alto livello.

![[UniPi-Appunti/Studi/Triennale Informatica/3° Anno/Reti - lab 3/Media/Untitled 1 1.png]]

