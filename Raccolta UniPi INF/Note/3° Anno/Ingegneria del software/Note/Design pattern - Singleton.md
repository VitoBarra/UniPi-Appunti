---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Singleton
---
tipo di [[GoF Design Patterns]]  Creazionale

un pattern 

### quando usarla 
- Quando si vuole una sola instanza di  on oggetto 
- Quando Ci serve un instanza di facile accesso
#### Struttura
![[A7C22272-3D6A-4E4F-9D24-8D5A7622431B.jpeg]]

##### Componenti
un riferimento statico della tipo della classe di cui si vuole fare il singleton.


## Lazy inizialization
Un singleton Si puo inizializzare in modo lo Lazy ovvero 

  ```java
  public void getInstance()
  {
	  return _instance== null ? new Singleton() : _instance
  } 
  ```
cosi facendo si puo ritardare una inizializazione che puo essere costata ma questo puo portare problemi in un contesto di multiThreading. se due thread diversi chiamano insieme getInstance() potrbbero entrambi creare un instanza cosi facendo c è ne sarebbero due diverse nel sistema.

#### SOluzioni
1. non usare inizializazione lazy e inizializzare subito il SIngleton
2. Tecniche di sincronizzazione per il get instance cosa costosa in termini di performance 
3. Double- Checked_ locking: controllando due volte per sincronizare solo la prima inizializazione 
``` Java
public static Singleton getInstance()
{
	if(_instance == null)
		syncronized(Singleton.class)
		{
			if(_instance == null)
			_instance = new Singleton();
		}
	return _instance;
}
```

### sotto classi di Singleton

con le sotto classi abbiamo un rapporto esclusivo di instanza c è ne puo essere una solo di qualsiasi tipo. per affrontare questa problematica con i singleton ci sono due metodi 
1. il metodo _GetInstance_(string type) Decide di quale sotto classe si deve creare l instanza tramite un parametro 
	- problematico perche puo rompere il principio [[Principio SOLID#S*O*LID: *O*pen Closed Principle| open Closed]]
	-  i costrutturi devono essere publici quindi il programmatore puo comunque coreane altre instanze 
2. Metodo static Instanciate();
	-  ogni sotto classe ha un metodo instanciate
	 ```Java
	
  public static SubSingleton instance() { 
	  if(uniqueInstance == null) 
	  uniqueInstance = new SubSingleton();
   return uniqueInstance ; }
	 ```
	- e la classe padre singleton puo usare _GetInstance_() per prendere quel instanza. 
		- L unico svantaggio e che se non si inizializza prima _GetInstance_(). potrebbe ritornare null

#### Vantaggi
1.  puoi passare gli oggetti come parametri 
2. puoi implementare interfacce o classi base
3. puo utilizzare con [[Design pattern - Factory | Design pattern  Factory]] per costruire intanze

#### Svantaggi
[svantaggi](https:// www.oracle.com Ingegneria del Software /technicalresources / articles /java/ singleton.html)