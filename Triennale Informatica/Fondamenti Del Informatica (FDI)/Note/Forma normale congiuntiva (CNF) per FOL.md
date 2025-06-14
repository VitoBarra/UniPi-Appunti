---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Forma normale congiuntiva (CNF) per FOL
---
Forma [[Forma normale congiuntiva (CNF)|Forma normale congiuntiva (CNF)]] estesa alla [[Logica del primo ordine (FOL)|logica del primo ordine]] 

l'Algoritmo per trasformare un arbitrario enunciato nella forma CNF è il seguente:
1. Eliminazione della $\iff:(A\iff B) \equiv (A \implies B) \land (B \implies A)$
2. Eliminazione  dell $\implies : (A \implies B) \equiv (\lnot A \lor B)$
3. Negazione All interno 
	1. $\lnot(A \lor B) \equiv (\lnot A \land \lnot B)$
	2. $\lnot(A \land B) \equiv (\lnot A \lor \lnot B)$
	3. $\lnot \forall x. A \equiv \exists x . \lnot A$
	4. $\lnot \exists x . A \equiv \forall x. \lnot A$
4. standardizzazione delle variabili, ogni quantificatore ha una variabile nominata in modo diverso (per evitare collisioni)
5. [[Riduzione da FOL ad logica proposizionale|Skolemizzazione]] delle variabili
6. portiamo tutte i quantificatori in forma premessa
	1. $(\forall x. A) \lor B\equiv \forall x.(A \lor B)$
	2.  $(\forall x. A) \land B\equiv \forall x.(A \land B)$
	3. equivalente se $B$ non contiene x
7. eliminiamo i quantificato universali, sotto l assunzione che ogni variabili libera si  universalmente quantificata 
8. algoritmo normale per trasformare le formule a clausole 
9. si rinominato le variabili con nomi diversi se sono in clausole diverse
tutti questi passi preservano l equivalenza delle formule tranne la _[[Riduzione da FOL ad logica proposizionale|Skolemizzazione]]_
