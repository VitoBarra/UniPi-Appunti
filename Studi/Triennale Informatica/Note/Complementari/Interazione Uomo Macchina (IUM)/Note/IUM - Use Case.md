---
type: nota
course: Interazione Uomo Macchina
topic: 
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# IUM - Use Case
---
gli _user case_ (_caso d uso_) è una descrizione accurata e dettaglia del interazione che ha l utente con il sistema per ottenere un certo goal.

ogni _caso d uso_ è una sequenza di semplici passi che l utente fa per ottenere il suo goal e come reagisce il sistema ad ogni suo passo.


rispetto agli [[IUM - Scenario|scenari]] gli use case sono più granulari infatti spesso ad ogni _scenario_ sono assegnati più _use case_

gli _use case_ sono importanti siccome spiegano come il sistema dovrebbe reagire al interazione

![[Pasted image 20230609175635.png]]

gli elementi dei _casi d uso_ sono
- _attori_: qualcuno o qualcosa che esegue un comportamento
- _stakehlder_: qualcuno o qualcosa che ha qualche interessa nel system under discussion (SUD)
- _attore primario_: stakeholder che inizia l interazione con il sistema con un obiettivo
- _precondizioni_: cosa deve essere vero prima che il caso d uso possa essere avviato
- _trigger_: quale evento fa partire questo caso d uso
- _Main success scenbario \[basic flow\]_: la sequenza di passi principale che porta al raggiungimento del obiettivo
- _percorsi alternativi \[alternative flow\]_: sequenza di passi alternativa solitamente se si prende un percorso diverso per arrivare al obiettivo o qualcosa va storto



#### Metodo per la scrittura del caso d uso
Kenworthy (1997)
1. Identify who is going to be using the website. 
2.  Pick one of those users. 
3.  Define what that user wants to do on the site. Each thing the use does on the site becomes a use case. 
4.  For each use case, decide on the normal course of events when that user is using the site
5.  Describe the basic course in the description for the use case. Describe it in terms of what the user does and what the system does in response that the user should be aware of.
6.  When the basic course is described, consider alternate courses of events and add those to "extend" the use case. 
7.  Look for commonalities among the use cases. Extract these and note them as common course use cases. 
8.  Repeat the steps 2 through 7 for all other users.