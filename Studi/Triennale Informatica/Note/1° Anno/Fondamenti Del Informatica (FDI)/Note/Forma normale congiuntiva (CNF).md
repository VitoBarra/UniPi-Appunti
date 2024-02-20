---
Course: "[[Fondamenti Del Informatica (FDI)]]"
Subject: 
Area: 
Topic: 
SubTopic: 
tags:
  - FDI
---

# Forma normale congiuntiva (CNF)
---
è una modo per rappresentare l espressioni preposizionali della [[Logica proposizionale|Logica]] utilizzando congiunzione ($\land$ and) di disgiunzione ($\lor$ or) 
si avrà quindi qualcosa del tipo 
$$(l_1 \lor l_2  \lor\dots) \land (l_n \lor l_m  \lor\dots) \land \dots$$
gli operandi della congiunzione, ovvero la parti tra parentesi, sonno dette _clausole_ 

#### Proprietà
- Questa forma non è restrittiva è sempre possibile ottenerla da un espressione in un altra forma preservando l uguaglianza logica 
- la forma a clausole _NON_ è unica, la stessa espressione logica puo essere espressa con piu formule a clausole


##### vantaggi
-  SI puo utilizzare la notazione insiemistica  $\{l_1,l_2,\dots\}\{\dots\}\dots$  siccome l ordine delle disgiunzioni (_interne in un insieme_) e delle congiunzioni (_tra gli insiemi_) non conta
- è una forma comoda per fare shortening del [[Calcolo proposizionale (PROP)|Calcolo proposizionale]] 
	- si puo terminare prima se si trova anche un solo _letterale_ vero al interno di una clausola
	- si puo terminare prima se si trova anche una sola _clausola_ falsa  

### Algoritmo per la trasformazione a clausole
1. Eliminazione della $\iff:(A\iff B) \equiv (A \implies B) \land (B \implies A)$
2. Eliminazione  dell $\implies : (A \implies B) \equiv (\lnot A \lor B)$
3. Negazione All interno 
	1. $\lnot(A \lor B) \equiv (\lnot A \land \lnot B)$
	2. $\lnot(A \land B) \equiv (\lnot A \lor \lnot B)$
4. Distribuzione di $\lor$ su $\land$
	1. $(A \lor (B \land C)) \equiv ( A \lor B) \land (A \lor C)$



## Forma a clausole per FOL
è un estensione della forma a clausole fatta per funzionare con la [[Logica del primo ordine (FOL)|Logica del primo oridne]]

### Algoritmo per la trasformazione a clausole
1. Eliminazione della $\iff:(A\iff B) \equiv (A \implies B) \land (B \implies A)$
2. Eliminazione  dell $\implies : (A \implies B) \equiv (\lnot A \lor B)$
3. Negazione All interno 
	1. $\lnot(A \lor B) \equiv (\lnot A \land \lnot B)$
	2. $\lnot(A \land B) \equiv (\lnot A \lor \lnot B)$
	3. $\lnot \forall x. A \equiv \exists x . \lnot A$
	4. $\lnot \exists x . A \equiv \forall x. \lnot A$
4. standardizzazione delle variabili, ogni quantificatore ha una variabile nominata in modo diverso (per evitare confusioni )
5. Skolemizzazione delle variabili
6. portiamo tutte i quantificatori in forma prenessa
	1. $(\forall x. A) \lor B\equiv \forall x.(A \lor B)$
	2.  $(\forall x. A) \land B\equiv \forall x.(A \land B)$
	3. equivalente se $B$ non contiene x
7. eliminiamo i quantificato universali, sotto l assunzione che ogni variabili libera si  universalmente quantificata 
8. algoritmo normale per trasformare le formule a clausole 
9. si rinominato le variabili con nomi diversi se sono in clausole diverse
tutti questi passi preservano l equivalenza delle formule tranne la _[[Sistema di inferenza per FOL#Skolenizazione|Skolemizzazione]]_


