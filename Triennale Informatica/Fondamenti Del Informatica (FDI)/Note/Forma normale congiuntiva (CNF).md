---
Course: "[[Fondamenti Del Informatica (FDI)]]"
Area: 
topic: 
SubTopic: 
tags:
  - FDI
---

# Forma normale congiuntiva (CNF)
---
la **Forma normale congiuntiva (CNF)** è una modo per esprimere l' [[Logica proposizionale|enunciati logici]] in modo come **congiunzioni**($\land$ and) di **disgiunzioni**($\lor$ or) la forma generale è un espressione del tipo:  $$(l_1 \lor l_2  \lor\dots) \land (l_n \lor l_m  \lor\dots) \land \dots$$gli operandi della congiunzione, ovvero la parti tra parentesi, sonno dette **_clausole_** 

le proprietà di questa formulazione sono:
- Questa forma non è restrittiva è sempre possibile ottenerla da un espressione in un altra forma preservando l uguaglianza logica 
- la forma a clausole _NON_ è unica, la stessa espressione logica puo essere espressa con piu formule a clausole

alcuni dei vantaggi:
-  SI puo utilizzare la notazione insiemistica  $\{l_1,l_2,\dots\}\{\dots\}\dots$  siccome l ordine delle disgiunzioni (_interne in un insieme_) e delle congiunzioni (_tra gli insiemi_) non conta
- è una forma comoda per fare shortening del [[Logica proposizionale|Calcolo proposizionale]] 
	- si puo terminare prima se si trova anche un solo _letterale_ vero al interno di una clausola
	- si puo terminare prima se si trova anche una sola _clausola_ falsa  


l'algoritmo per trasformare un **arbitrario enunciato** nella **forma normale congiuntiva**:  
1. Eliminazione della $\iff:(A\iff B) \equiv (A \implies B) \land (B \implies A)$
2. Eliminazione dell $\implies : (A \implies B) \equiv (\lnot A \lor B)$
3. Negazione All interno 
	1. $\lnot(\lnot A)$
	2. $\lnot(A \lor B) \equiv (\lnot A \land \lnot B)$
	3. $\lnot(A \land B) \equiv (\lnot A \lor \lnot B)$
4. Distribuzione di $\lor$ su $\land$
	1. $(A \lor (B \land C)) \equiv ( A \lor B) \land (A \lor C)$


