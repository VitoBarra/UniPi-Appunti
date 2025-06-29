---
Corse 1: "[[Fondamenti Del Informatica (FDI)]]"
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - FDI
  - IA
  - AIF
Area: 
topic: nota
SubTopic:
---

# Logica
---
La **logica** costituisce il fondamento formale per determinare la validità di **inferenze** e **ragionamenti**. Essa si articola nello studio delle strutture formali attraverso cui si possono esprimere proposizioni e stabilire relazioni tra esse, indipendentemente dal contenuto specifico delle affermazioni.

i concetti di base della **logica** sono: i **valori di varità** $\{True,False\}$ e la **proposizione** (o **enunciato**) questa è un espressione che può prendere valori **verità**. Una **preposizione elementare** è il tipo più semplice di **preposizione** e si solitamente indicano utilizzando simboli (es. $\alpha$) a cui si può assegnare un **valore di verità** (es. $\alpha=True$).

Tramite l'utilizzo di un [[Linguaggi formali|linguaggio formale]] per la **logica** si possono costruire **preposizioni complesse** combinando le **proposizioni elementari** con **connettivi logici**. ogni connettivo è un [[Operazioni con sottospazi|operatore]] che accetta **valori di verità** e restituisce **valori di vertia**. 

Dato un **enunciato** $\alpha$ un **modello** è un assegnamento alle sue componenti che concretizzano il valore di $\alpha$ come $True$ o $False$ senza ambiguità.

se $\alpha = True$ nel modello $m$ allora si dice che $m$ **soddisfa** $\alpha$ e si indica con $M(\alpha)$ l'insieme di tutti i **modelli** che soddisfano $\alpha$.


Alcuni esempi [[Linguaggi formali|linguaggi formali]] usati per la logica sono:
- Il [[Logica proposizionale|Calcolo proposizionale]] si limita all'analisi delle combinazioni tra proposizioni atomiche tramite connettivi
- [[Logica del primo ordine (FOL)|logica del prim ordine]] introduce variabili, quantificatori e relazioni, consentendo di esprimere proprietà più generali e strutture complesse.

##### Deduzione (o conseguenza logica)
Nella [[logica|logica]] una **deduzione** (o **conseguenza logica**) è una **conclusione**, sotto forma di **enunciato** che discende necessariamente dalle **premesse**. Ovvero assumendo **vere** le premesse, la conclusione non può che essere **vera** indipendentemente dal contenuto specifico delle proposizioni coinvolte. 

**sino** $\alpha , \beta$ due **enunciati** 
**allora** si dice che $\beta$ è **Conseguenza logica** (o **entailment**) di $\alpha$ indicato con $$\alpha \models \beta$$**se** in ogni modello in cui $\alpha$ risulta $True$, anche $\beta$ è $True$, ovvero vale che $M(\alpha) \subseteq M(\beta)$.






