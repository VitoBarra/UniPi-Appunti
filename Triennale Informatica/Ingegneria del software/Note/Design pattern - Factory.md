---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Factory
---

tipo di [[GoF Design Patterns]] creazionale

in generale fornisce modi per costruire oggetti senza l utilizzo del _new_. siccome questo ultimo rompe sia il  principio  [[Principi SOLID#S*O*LID: *O*pen Closed Principle|Open Close]]  che quello di [[Principi di progettazione e qualità di un progetto#Information HIding|information Hiding]]
siccome rende le classi dipendenti dai i tipi specifici delle classi instansiate. e ne classò di selezione di quale classe instanziate se dovesse cambiare la scelta aggiungendo o rimuovendo classi quel codice dove cambiare di nuovo 

## Simple Factory (o Concrete Factory)
#### Struttura
![[05661C72-1F02-4A0B-8D4A-21C741AC8DDA.jpeg]]
con questo pattern la classe che richiede la costruzione di un oggetto mantiene un riferimento ad un classe factory che gestisce la gestione della creazione degli oggetti. è meglio di non far nulla ma non flessibile come potrebbe essere

## Factory Method
Pattern che gestisce la creazione degli oggetti basandosi sul [[Eridarieta Delle classi|Eridarieta Delle classi]] 
### Quando Usarlo 
- applicabile quando una classe non po' anticipare la classe del oggetto che deve creare
#### Struttura
![[927B0B05-F67D-403D-A092-A49E6F1BC2F1.jpeg]]
in questo pattern il FactoryMethod lascia scegliere il prodotto concreto da istanza alla sottoclasse di creator. in questo modo ogni sottoclasse avrà il suo prodotto associato
##### Componenti
- _Product_: Definisce l interfaccia per i tipi che il factoryMethod Costruisce
- _ConcreteProduct_: Implementa l interfaccia del prodotto
- _Creator_ :  Dichiara il metodo che istanzia l oggetto di tipo Product
- _ConcreteCreator_: fa l override del factoryMethod e ritorna un Istanza di ConcreteProduct

### Vantaggi
- codice più flessibile e riusabile grazie al eliminazione del istanza specifica
##### richiede
chi vuole instanziate un prodotto concreto deve creare una sottoclasse
##### problema di implementazione
- Se il il factory method può costruire più di un tipo di oggetto allora il factoryMethod deve avere un parametro.



## Abstract Factory
Pattern che gestisce la creazione degli oggetti basandosi sul [[Delega VS Eredarieta|Delega]] 
### Quando Usarlo
quando si vuole aggiungere flessibilità rispetto ai factory method e si hanno piu oggetti da istanziare correlati tra di loro.
#### Struttura
![[C25A38D6-E770-451C-98F1-D31722D9EEA4.jpeg]]
in questo pattern l oggetto a cui servono gli oggetti delega la costruzione mantenendo un interfaccia di una factory che li costruisce. ogni oggetto concreto che implementa la AbstractFactory costruisce famiglie di oggetti o oggetti correlati tra loro.
In generale é molto simile al Factory Method
![[68ACFE3C-1187-472D-BB1C-0D88B71DA129.jpeg]]

##### Componenti
- _AbstractProduct_: Definisce l interfaccia per i tipi  che producono le factory
- _ConcreteProduct_: Implementa l interfaccia del prodotto
- _AbstractFactory_ :  Dichiara i metodi  interfaccia che devono instanziare un AbstractProduct
- _ConcreteFactory_: implementa i metodi Della AbstarcFactory instanziando oggetti della stessa famiglia o correlati tra loro

### Vantaggio
- codice più flessibile e riusabile grazie al eliminazione del istanza specifica




le factory sono di solito  [[Principi GRASP#Pure Fabrication|Pure Fabrication]]
