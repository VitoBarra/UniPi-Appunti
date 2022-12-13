---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - State
---

tipo di [[GoF Design Patterns]] comportamentale

Permette all oggetto di comportarsi in modo diverso in base allo stato interno 


### Quando applicarlo
1. Il comportamento di un oggetto dipende dal suoi stato e deve cambiare il suo comportamento a run time in base allo stato 
2. Le operazioni hanno dichiarazioni condizionali complesse che dipendono dallo stato del oggetto. 
#### Come Applicarla
1. utilizzare una classe che funga da macchina a stati per il cliente il “Context” che tiene un riferimento di tipo _State_ che rappresenta lo stato corrente
2. Creare una classe base _State_ che rispecchi l interfaccia delle operazioni sulla macchina a stati. questa ha bisogno di una parametro di riferimento a context e specifica i comportamenti di default.
3. Derivare La classe _State_ definendo le operazioni e le transizioni di stato 
4. tutte le richieste al context vengono delegate al oggetto satate
5. i metodi del oggetto state cambiano il contesto

### Vantaggi
- più facile aggiungere nuovi stati se necessario
- più facile da capire
- salvataggio dello stato corrente in un unico posto
- comportamento dello stato incapsulato
##### passivita
- stati dipendenti tra loro siccome ogni stato deve conoscere i suoi prossimi 	

#### Struttura
![[F684B1BD-A085-4045-87D1-14EC76A5DC6F.jpeg]]
##### Componenti
_Cointext_: 
- definisce l interfaccia
- mantiene l Istanza di concrete state
_State_:  Definisce l interfaccia del comportamento di uno specifico stato, eventualmente può a avere un comportamento di default
_ConcreteState_: Implementa l interfaccia state


### Exemple 
![[4FD5B704-A5A0-45EF-B4F3-3A8426C94025.jpeg]]

 