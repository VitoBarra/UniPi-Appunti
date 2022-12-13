---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Principi SOLID
---
_SOLID_:
- **S**ingle Responsibility Principle 
	- Una classe(o metodo) dovrebbe avere solo un motivo per cambiare. 
- **O**pen Closed Principle
	- Estendere una classe non dovrebbe comportare modifiche alla stessa.
- **L**iskovSubstitution Principle 
	- Istanze di classi derivate possono essere usate al posto di istanze della classe base. 
- **I**nterface Segregation Principle 
	- Fate interfacce a grana fine e specifiche per ogni cliente.
- **D**ependency Inversion Principle
	- Programma guardandole interfacce non l’implementazione. 

### **S**OLID: **S**ingle ResponsibilityPrinciple
ogni classe deve avere un solo motivo per cambiare. 
- un motivo è una responsabilità.

questo principio ci dice che se abbiamo 2 motivi per cambiare la classe allora questa andrebbe divisa in due classi. 

Esiste un eccezione: se non si può cambiare una delle due responsabilità dell applicazione senza cambiare contestualmente anche altra allora separare introdurrebbe una complessità non necessaria 


### S**O**LID: **O**pen Closed Principle
- Le entità software (classi moduli e funzioni ) devono essere aperte per estensione ma chiuse per modifiche. 
	- che significa che i moduli già scritti devono essere scritti in modo che non debbano essere cambiati ma solo estesi.
questo si realizza utilizzando le classi astratte e le implementazioni di quelle classi e la delega. 
un esempio di Delega è il design pattern [[Design pattern - Strategy|Strategy]]

### SO**L**ID: **L**iskov substutition principle
 il principio dice: Se $S$ è sotto tipo di $T$, allora per ogni oggetto o1 di tipo $S$ esiste un oggetto o2 di tipo $T$, tale che, dato un qualsiasi programma $P$ definito in termini di $T$, il comportamento di $P$ è immutato quando o1 è usato al posto di o2.
 _riassumendo_: le classi derivate devono potersi sostituire alle classi base.

## SOL**I**D: **I**nterface Segregation Principle
interfaccia a grana fine e specifiche per ogni cliente.
- i Clienti non devono dipendere da interfacce che non usano
in pratica evitare di creare interfaccia troppo grandi dove non necessariamente tutti i metodi di quel interfaccia servono in tutte le sue implementazioni. nel caso si risolve dividendo le interfacce 

## SOLI**D**: **D**ependency Inversion Principle
i moduli di alto livello non devono dipendere da quelli di basso livello
- entrambi devono dipendere da astrazioni
- le astrazione non devono dipendere dai dettagli ma il contrario 
detto in altre parole non ci si deve basare sulle implementazioni specifiche ma sulle astrazioni. ragionare in questi termini permette il disaccoppiamento 
##### esempio 
![[C8638C83-F1AE-4A9B-B1E1-521856DD7B38.jpeg]]

