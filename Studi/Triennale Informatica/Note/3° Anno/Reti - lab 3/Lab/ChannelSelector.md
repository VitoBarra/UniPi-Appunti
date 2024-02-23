---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# ChannelSelector
---
un _Selector_  è una classe [[java]] che server per gestire una selezioni di [[Channel NIO]] in modalita non bloccante con notifiche di attività quando c è necessita di fare delle operazioni.
lo si puo utilizzare per creare server signole thread efficenti evitando di consumare risorse per gestire piu thread.
un singolo thread puo gestire un numero arbitrario di socket
- meno costo overhead
- piu scalabilita
![[Pasted image 20230112012753.png]]

### Strutura
![[Pasted image 20230112013147.png]]
#### Apertura
si apre con 
```java
Selector selector = Selector.open();
```
si possono registrare al selector solo i tipi di channel che derivano da _selectableChannel_ quindi:
-  ServerSocketChannel 
- SocketChannel 
- DatagramChannel 
- Pipe.SinkChannel 
- Pipe.SourceChannels

#### Registrazione
per registrarli al _selector_ si utilizza 
```java
Selectionkey key = channel.register(selector, ops, attach);
```
dove _ops_ sono gli operatori e sono gestiti da una maschera di 8 bit che rapresentano le operazioni a cui si è interessati aspettare la notifica
![[Pasted image 20230112013559.png]]
manipolando le operazioni con operatori bit a bit si possono creare maschere di più operatori _ma_ non tutti i tipi di canali supportano tutte le operazioni
- es. _SocketChannel_ non supporta _accept_
nella pratica si utilizzano le costati statiche definite in _slectionKey_ per costruire la maschera di bit
![[Pasted image 20230112013837.png]]
```java
Selectionkey key = channel.register(selector,SelectionKey.OP_READ | SelectionKey.OP_WRITE);
```
ad ogni registrazione il metodo ritorna un oggetto _SelectionKey_ che contiene
- _il canale_ a cui si riferisce 
- _il selettore_ a cui si riferisce 
- _l'interest set_ 
	- utilizzato quando il metodo select viene invocato per monitorare i canali del selettore 
	- definisce le operazioni su cui si deve fare il controllo di “readiness”, 
- il _ready set_ 
	- dopo la invocazione della select, contiene gli eventi che sono pronti su quel canale  
- un allegato, _attachment_ 
	- uno spazio di memorizzazione associato a quel canale per quel selettore

un canale può registrarsi più volte sullo stesso selettore


#### Select
si avvia la selezione con 
```java
int selector.select( ); 
```
questa è
- bloccante, seleziona, tra i canali registrati sul selettore selector, quelli pronti per almeno una delle operazioni dell'interest set. 
- si _blocca_ fino a che una delle seguenti condizioni è vera 
	- almeno un canale è “pronto” 
	- il thread che esegue la selezione viene interrotto 
	- il selettore viene sbloccato mediante il metodo wakeup() 
- restituisce il numero di canali pronti che hanno generato un evento dopo l'ultima invocazione della select() 
- costruisce un insieme contenente le SelectionKeys dei canali pronti 
```java
int selector.select(long timeout)
```
- si blocca fino a che non è trascorso il timeout, oppure vale una delle condizioni precedenti 
```java
int selector.selectNow(long timeout)
```
- non bloccante, nel caso nessun canale sia pronto restituisce il valore 0


quando uno dei cannali manda una notifica di attività su una delle operazioni impostate come "ineteressanti" cambia il _ReadySet_ della _Selectionkey_ di quel canale inserendo l'operazione della notifica.

per controllare quale operazione è pronta si 
1. Controllare la bit mask
```java
if ((key.readyOps( ) & SelectionKey.OP_READ) != 0)
```
2. usare shortcut equivalenti
```java
key.isReadable()
```

##### Componenti della Select
- _Key Set_: 
	- _SelectionKeys_ dei canali registrati con quel selettore. 
	- restituito dal metodo keys() 
- _Selected Key Set_ :
	- restituito dal metodo selectedKeys(),invocato sul selettore 
	- insieme di chiavi precedentemente registrate tali per cui una delle operazioni nell'interest set è pronta per l'esecuzione 
	- dopo una select() consente di accedere ai canali pronti per l'esecuzione di qualche operazione 
- _Cancelled Key Set_: 
	- chiavi che sono state cancellate (quelle su cui è stato invocato il metodo cancel(), ma il cui canale è ancora registrato sul selettore)


##### Fasi della select
1. “_delayed cancellation_”: cancella ogni chiave appartenente al _Cancelled Key Set_ dagli altri due insiemi. 
2. interagisce con il sistema operativo per verificare lo stato di “_readiness_” di ogni canale registrato, per ogni operazione specificata nel suo _interest set_. 
3. per ogni canale con almeno una operazione “ready” 
	- _if_ il canale già esiste nel _Selected Key Set_ 
		- aggiorna il _ready set_ della chiave corrispondente: calcola l'or bit a bit tra il valore precedente del ready set e la nuova maschera 
		- i bit ad 1 si “_accumulano_” con le operazioni pronte. 
	- _else_  
		- resetta il ready set e lo imposta con la chiave della operazione pronta 
		- aggiunge la chiave al _Selected Key Set_


- “comportamento cumulativo” della selezione 
	- una chiave aggiunta al _selected key set_, può essere rimossa solo con una operazione di rimozione esplicita 
	- il ready set di una chiave inserita nel _selected key set_, non viene mai resettato, ma viene aggiornato incrementalmente 
	- scelta di progetto: assegnare al programmatore la responsabilità di aggiornare esplicitamente le chiavi 
	- per resettare il ready set 
		- rimuovere la chiave dall'insieme delle chiavi selezionate

#### Pattern generlae
```java
Selector selector = Selector.open();
channel.configureBlocking(false);
SelectionKey key = channel.register(selector, SelectionKey.OP_READ);
while(true) 
{
	int readyChannels = selector.selectNow();
	if(readyChannels == 0) continue;
	Set selectedKeys = selector.selectedKeys(); 
	Iterator keyIterator = selectedKeys.iterator();
	while(keyIterator.hasNext()) 
	{
		SelectionKey key = keyIterator.next();
		if(key.isAcceptable()) 
		{ // a connection was accepted by a ServerSocketChannel. } 
		else if (key.isConnectable()) { // a connection was established with a remote Server (client side) }
		else if (key.isReadable()) { // a channel is ready for reading }
		else if (key.isWritable()) { // a channel is ready for writing }
		keyIterator.remove(); 
}}
```
_keyIterator.remove_() deve essere invocata, poiché il _Selector_ non rimuove automaticamente le chiavi dal _selected key set_ 

#### Attachment
impostato alla registrazione della chiave
_attachment_: riferimento ad un generico Object 
- utile quando si vuole accedere ad informazioni relative al canale (associato ad una chiave) che riguardano il suo stato pregresso 
- necessario perchè le operazioni di lettura o scrittura non bloccanti non possono essere considerate atomiche 
	- nessuna assunzione sul numero di bytes letti 
- consente di tenere traccia di quanto è stato fatto in una operazione precedente. 
	- l'attachment può essere utilizzato per accumulare i byte restituiti da una sequenza di letture non bloccanti 
	- memorizzare il numero di bytes che si devono leggere in totale.
