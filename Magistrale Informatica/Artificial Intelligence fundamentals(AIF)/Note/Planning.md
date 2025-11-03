---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning
---
il **Planning Classico** è definito come il compito di individuare una **sequenza di azioni** per raggiungere un obiettivo in un ambiente **discreto**, **deterministico**, **statico e completamente osservabile**, questo per essere fatto anche con [[Problem-Solving Agent| agenti per fare problem solving]] e [[Agenti Knowledge Based|agente logico ibrido]] ma entrambi presentano due limitazioni:
- richiedono euristiche ad hoc per ciascun dominio 
- necessitano di rappresentare esplicitamente uno spazio di stati esponenzialmente grande.
Per superare queste limitazioni, si puo usare una [[Rappresentazione del ambiente|factored rapresentation]] chiamata **[[Planning - Planning Domain Definition Language (PDDL)|Planning Domain Definition Language (PDDL)]]**

, questa rappresentazione è basta sulla [[Logica del primo ordine (FOL)|logica del promo ordine]] ed è in grado di descrivere molte **azioni possibili** con un unico **schema di azione** senza conoscenze specifiche del dominio. 
il **PDDL** di base gestisce domini di **pianificazione classici**, mentre le estensioni supportano domini non classici ovvero , [[Definizione di Problemi-Ambienti|continui, parzialmente osservabili, concorrenti e multi-agente]]. 

In **PDDL** le componenti principali sono:
- **Stato**: è rappresentato come una congiunzione di **fluents atomici ground**. 
	- **Ground**: significa senza variabili,
	- **fluent**: indica un aspetto del mondo che cambia nel tempo, 
	- **ground atomic**: significa predicato singolo con argomenti costanti.
**PDDL** utilizza la [[FOL - Semantica Database|semantica database]]: l'assunzione di mondo chiuso implica che i fluents non menzionati siano falsi, e l'assunzione di nomi unici distingue oggetti 

Uno **schema di azione** rappresenta una **famiglia di ground action** ad esempio:$$
\begin{align*}
\text{Action}(&\text{Fly}(p, \text{from}, \text{to}), \\
&\text{PRECOND: } \text{At}(p, \text{from}) \land \text{Plane}(p) \land \text{Airport}(\text{from}) \land \text{Airport}(\text{to}) \\
&\text{EFFECT: } \neg\text{At}(p, \text{from}) \land \text{At}(p, \text{to}))
\end{align*}
$$ovvero dove le componenti sono 
- $Action(x,y,z,\dots)$: **Action name** con una list di tutte le variabili usate nello schema   
- $PRECOND$: una lista di **precondizioni**, e sono una lista di predicati sia positivi che negativi 
- $EFFECT$: una lista di **effetti**, e sono una lista di predicati sia positivi che negativi
**ogni variabile** presente negli **effetti** di uno schema deve comparire anche nelle **precondizioni**

l'istanziazione con costanti produce un'**azione ground**:$$
\begin{align*}
\text{Action}(&\text{Fly}(P1, SFO, JFK)), \\
&\text{PRECOND: } \text{At}(P1, SFO) \land \text{Plane}(P1) \land \text{Airport}(SFO) \land \text{Airport}(JFK) \\
&\text{EFFECT: } \neg\text{At}(P1, SFO) \land \text{At}(P1, JFK)
\end{align*}
$$
Un'**azione ground** $a$ è **applicabile** in uno stato $s$ se $s$ ha come [[Conseguenza Logica (Deduzione)|conseguenza logica]] le precondizioni di $a$, ovvero tutti i letterali positivi delle precondizioni sono in $s$ e quelli negati non lo sono. 
L'applicazione di $a$ in $s$ produce uno stato $s'$:$$
RESULT(s, a) = (s - DEL(a)) \cup ADD(a)
$$dove 
- $DEL(a)$ è la lista dei **fluents negati** negli effetti
- $ADD(a)$ la lista dei **fluents positivi** negli effetti 

Una **collezione di schemi d'azione** definisce un **dominio di pianificazione**. Un problema specifico è definito aggiungendo uno
- **Stato iniziale**: Lo **stato iniziale** $s_i$ è una congiunzione di **fluents atomici ground**.
- **Obiettivo**: L'obiettivo $goal$ può avere letterali positivi o negativi e possono contenere variabili