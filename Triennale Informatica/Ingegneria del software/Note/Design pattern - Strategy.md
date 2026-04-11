---
Course: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Strategy
---
tipo di [[GoF Design Patterns]] comportamentale

### Quando usarlo
quando si deve definire un numero indefinito di variazioni di un algoritmo o di un comportamento 
- oggetti simili che variano solo per il comportamento 
- servono più varianti di un algoritmo
- una classe espone molti comportamento ma questi vengono selezionati con molte condizioni questa logica si può semplificare spostando le condizioni nella strategia. 
#### come si applica
- incapsulando le variazioni in classi separate
- c è un accesso uniforme al comportamento (un interfaccia)
### Vantaggi
- l algoritmo diventa molto indipendente dal client che lo utilizza
- le varie variazioni sono intercambiabili dinamicamente
- da un alternativa alla creazioni di molte sottoclassi 
- elimina sequenze di condizioni molto lunghe
- da una scelta di implementazioni diverse per lo stesso comportamento 
##### Richiede
- il numero di oggetti può aumentare molto 
#### Struttura
![[IMG - Design pattern - Strategy 1.jpeg]]
##### Didascalia
1. _Strategy_: definisce un interfaccia comune agli algoritmi supportati 
2. _ConcreteStragety_: ogni implementazione concreta del algoritmo
3. _Context_: 
	- Contiene una reference di tipo Strategy
	-  puo definire un interfaccia che lascia strategia l accesso dai dati  invece di passarli come argomento 


## Esempi 
1. ![[IMG - Design pattern - Strategy 2.jpeg]]
2. ![[IMG - Design pattern - Strategy 3.jpeg]]
