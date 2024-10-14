---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Channel NIO
---
il channel NIO (New Input Output) sono un sistema per la gestione del input-out 
che funzionano diversamente dai [[Stream IO]]  in partciolare

![[Pasted image 20230111201823.png]]
I canali sono entità create dal [[Sistemi Operativi|sistema operativo]]  questi sono:
- Bidirezionali 
- possono essere non-bloccanti
i canali non sono ad accesso diretto al programma ma scrivono su di un buffer e questo poi comunicherà con il programma 
il nome della classe del buffer utilizzato è  _Bytebuffer_ ed è l interfaccia di comunicazione tra canale e programma.

i canali sono connessi a descrittore di file/socket gestiti dal [[Sistemi Operativi| Sistema operativo]]

## Funzionamento del Buffer
![[Pasted image 20230111203000.png]]
un _Bytebuffer_ ha come struttura dati sottostante un byte array e delle variabili di stato 

#### Stato
- _Capacity_: 
	- massimo numero di elementi del Buffer 
	- definita al momento della creazione del Buffer, _non_ può essere modificata 
	- _java.nio.BufferOverflowException_, se si tenta di leggere/scrivere in/da una $posizione > Capacity$ 
- _Limit_:
	- indica il limite della porzione del Buffer che può essere letta/scritta 
		- per le scritture $limit = capacity$ 
		- per le letture delimita la porzione di Buffer che contiene dati significativi 
	- aggiornato implicitamente dalla operazioni sul buffer effettuate dal programma o dal canale 
- _Position_: 
	- come un file pointer per un file ad accesso sequenziale  
	- posizione in cui bisogna scrivere o da cui bisogna leggere  
	- aggiornata implicitamente dalla operazioni di lettura/scrittura sul buffer effettuate dal programma o dal canale  
- _Mark_:
	- memorizza il puntatore alla posizione corrente 
	- il puntatore può quindi essere resettato a quella posizione per rivisitarla 
	- inizialmente è _undefined_ 
	- se si resetta un mark undefined: _java.nio.InvalidMarkException_ 
valgono per queste variabili di stato valgono sempre le seguenti relazioni:
	 $$ 0\leq mark \leq position \leq limit \leq capacity$$

#### Operazioni
![[Pasted image 20230111203859.png]]
![[Pasted image 20230111203908.png]]
![[Pasted image 20230111203915.png]]
![[Pasted image 20230111203926.png]]
![[Pasted image 20230111203934.png]]
![[Pasted image 20230111203941.png]]
![[Pasted image 20230111203948.png]]
![[Pasted image 20230111203957.png]]
![[Pasted image 20230111204007.png]]

#### Lettura dal buffer
```java
channel.read(buffer)
```
- non si specifica la quantita di byte da leggere
	- non si sanno quanti byte sono stati letti e quanti c è ne sono di significati sul buffer
![[Pasted image 20230111211552.png]]
una volta letti dalla sorgente si deve predisporre il buffer alla lettura utilizzando buffer._flip_() per poterne poi leggerne il contenuto
#### Scrittura buffer
```java
for (int i=0; i<message.length;++i)
	buffer.put(message[i])

buffer.flip();
channel.write(buffer)
```
- bisogna prima scrivere il messaggio sul buffer
- predisporre il buffer alla lettura utilizzando _Flip_()\
- scrivere sul canale con _write_(buffer)

### Interazione con il sistema operativo
![[Pasted image 20230111204041.png]]
- la JVM esegue una _read_() da stream o canale e provoca una system call (native code) 
- il kernel invia un comando al disk controller 
- il disk controller, via [[IO - DMA|DMA]] (senza controllo della CPU) scrive direttamente un blocco di dati nel [[Dual-Mode Operation|kernel space]] 
- i dati sono copiati dal kernel space nello user space (all'interno della [[JVM]]).



### Tipi di buffer
#### non diretti
![[Pasted image 20230111205145.png]]
creati con 
```Java
			byteBuffer buf = ByteBuffer.allocate(10);
```
- crea un buffer sia sul kernel che nello heap della JVM
	- Questo porta a dover fare due copie o due scritture 
	- più lento
	- collectable dal [[Garbage Collector]] della JVM
#### Diretto
	![[Pasted image 20230111205616.png]]
creati con 
```Java
			byteBuffer buf = ByteBuffer.allocateDirect(1024);
```
- trasferire dati tra il programma ed il sistema operativo, mediante accesso diretto alla kernel memory da parte della JVM 
- evita copia dei dati da/in un buffer intermedio prima/dopo l'invocazione del sistema operativo 
	- _vantaggi_:
		- migliore performance 
	- _svantaggi_: 
		- maggiore costo di allocazione/deallocazione 
		- il buffer non è allocato sullo heap. [[Garbage Collector]] non può recuperare memoria

>[!tip] Classi ponte
>Se si intende usare i channel in modo direzionale si possono usare le normali classi di [[Stream IO]] e utilizzare _getChannel_()

## Gerarchia delle classi channel in java
![[Pasted image 20230111210551.png]]

### Perche usare NIO
#### Vantaggi 
- definizione di primitive “più vicine” al livello del sistema operativo, aumento di performance  
- in generale: migliori prestazioni, in molti casi, ma da valutare 
#### Svantaggi
* primitive a più basso livello di astrazione 
* perdita di semplicità ed eleganza rispetto allo [[Stream IO]] 
* maggior difficoltà nella messa a punto del programma 
* prestazioni dipendenti dalla piattaforma su cui si eseguono le applicazioni
#### Altro
* ma anche primitive espressive, ad esempio per il multiplexing dei canali 
	* adatto per lo sviluppo di applicazioni che devono gestire un alto numero di connessioni di rete. 