---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Planning Domain Definition Language (PDDL)
---
il **Planning Domain Definition Language (PDDL)** è un **specific domain lenguage** che offre una [[Rappresentazione del ambiente|rappresentazione fattorizata]] per il [[planning|planning classico]], quindi [[Definizione di Problemi-Ambienti|osservabile e deterministica]]. Questa rappresentazione è basta sulla [[Logica del primo ordine (FOL)|logica del promo ordine]] ed è in grado di descrivere molte **azioni possibili** con un unico **schema di azione** senza conoscenze specifiche del dominio. 

In **PDDL** le componenti principali sono:
- **Stato**: è rappresentato come una congiunzione di **fluents atomici ground**. 
	- **Ground**: significa senza variabili,
	- **fluent**: indica un aspetto del mondo che cambia nel tempo, 
	- **ground atomic**: significa predicato singolo con argomenti costanti.
**PDDL** utilizza la [[FOL - Semantica Database|semantica database]]: l'assunzione di **mondo chiuso** implica che i fluents non menzionati siano falsi, e l'assunzione di nomi unici distingue oggetti 

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



#### Estensione  
Si può estendere **PDDL** per poter descrivere casi di [[Definizione di problemi-Ambienti|ambienti continui, parzialmente osservabili, concorrenti e multi-agente]].  
Per fare ciò, è possibile permettere alle azioni di contenere variabili nella loro specifica che non fanno parte della lista di variabili dichiarate nello schema dell’azione.  $$
\begin{aligned}
&\text{Action(RemoveLid}(can), \\
&\quad \text{PRECOND: } \text{Can}(can) \\
&\quad \text{EFFECT: } \text{Open}(can)) \\
\\
&\text{Action(Paint}(x,can), \\
&\quad \text{PRECOND: } \text{Object}(x) \land \text{Can}(can) \land \text{Color}(can,c) \land \text{Open}(can) \\
&\quad \text{EFFECT: } \text{Color}(x,c))
\end{aligned}
$$Nel secondo schema d’azione, **$\text{Action(Paint}(x,can))$** non contiene la variabile $c$, che tuttavia viene utilizzata nelle precondizioni e negli effetti.  
Questo viene fatto perché $c$ potrebbe, o non potrebbe, essere conosciuto al momento dell’azione: si tratta infatti di un’informazione ottenibile tramite le **percezioni**.  

Inoltre, si aggiunge un modello dei sensori, rappresentato dai **percept schema**.  
Un ***percept schema*** permette di specificare la relazione tra le condizioni del mondo e le percezioni che l’[[Agenti Razionali|agente]] può ricevere.  
La sua struttura generale è:$$
\begin{array}{l}
\text{Percept(Color}(x,c), \\
\quad \text{PRECOND: Object}(x) \land \text{InView}(x)) \\
\\
\text{Percept(Color}(can,c), \\
\quad \text{PRECOND: Can}(can) \land \text{InView}(can) \land \text{Open}(can))
\end{array}
$$in questi esempi, **$Percept$** rappresenta l’informazione percepita dall’agente, mentre **$PRECOND$** descrive la situazione del mondo che rende possibile tale percezione.  
Quando l’agente riceve un percetto, utilizza i *percept schema* per aggiornare il proprio **belief state**, eliminando tutti gli stati che non sono coerenti con le osservazioni ricevute.  

Oltre all’estensione semantica del linguaggio, cambiano anche le assunzioni epistemiche: non si adotta più la **Closed-World Assumption**, secondo la quale ciò che non è noto si considera falso, ma si utilizza la **Open-World Assumption**, in cui le variabili non presenti nel belief state sono considerate **sconosciute**.  