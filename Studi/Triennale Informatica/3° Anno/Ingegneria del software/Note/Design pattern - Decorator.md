---
Subject: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Decorator
---

tipo di [[GoF Design Patterns]]  Strutturale

### Quando Usarlo 
Quando siamo un una situazioni in cui c è bisogno di mixare comportamenti.
- applicare il pattern evita dover fare una sotto classe per ogni combinazione 
- ![[B14D6B98-3257-4880-819E-CED140BA8335.jpeg]]

### Vantaggi
- più flessibile rispetto ad usare eridarietà, siccome componiamo gli oggetti e possiamo farlo a run time invece che staticamente ereditando. 
- può essere usato per fare mix and match
- una proprietà può essere aggiunta più volte
	- può portare ad oggetti mal formati in caso questa debba essere unica
- facile aggiungere nuovi feature in modo incrementale
##### Svantaggi
- problemi di performance se i decoratori sono complessi e se ne usano troppi
- il componente e i decoratori non sono uguali dal punti di vista degli oggetti
- bisogna creare molti oggetti piccoli 
- difficile da debbugare

#### Struttura
![[B04D6621-942A-48EE-8E54-E9EE59693B68.jpeg]]
##### Componenti
1. _Componet_: Interfaccia del oggetto decorato 
2. _ConcreteComponent_: classe base che implementa il comportamento 
3. _Decorator_ :  Definisce un interfaccia e mantiene un riferimento ad un _component_ che può essere anche già decorato
4. _ConcreteDecorator_: definisce una nuova responsabilità 