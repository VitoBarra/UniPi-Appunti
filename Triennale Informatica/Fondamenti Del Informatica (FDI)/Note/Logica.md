---
Corse 1: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course: "[[Fondamenti Del Informatica (FDI)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - FDI
  - IIA
  - AIF
Area:
topic: nota
SubTopic:
---

# Logica
---
La **logica** costituisce il fondamento formale per determinare la validità di un **ragionamento** tramite **[[Sistemi di inferenza logica|inferenze]]**. Essa si articola nello studio delle strutture formali attraverso cui si possono esprimere proposizioni e stabilire relazioni tra esse, indipendentemente dal contenuto specifico delle affermazioni.

i concetti di base della **logica** sono: i **valori di verità** $\{True,False\}$ e l **enunciato** (o **proposizione**) questo è un espressione che può prendere valori **verità**. Una **preposizione elementare** è il tipo più semplice di **preposizione** e si solitamente indicano utilizzando simboli (es. $\alpha$) a cui si può assegnare un **valore di verità** (es. $\alpha=True$).

Dato un **enunciato** $\alpha$ un **modello** è un assegnamento alle sue componenti che concretizzano il valore di $\alpha$ come $True$ o $False$ senza ambiguità.

se $\alpha = True$ nel modello $m$ allora si dice che $m$ **soddisfa** $\alpha$ e si indica con $M(\alpha)$ l'insieme di tutti i **modelli** che **soddisfano** $\alpha$.

dato un **enunciato** $\alpha$ è detto: 
- __Tautologia__(**valido**): se è sempre  $True$ con ogni possibile __modello__ ovvero $\forall m \in M(\alpha)$
- __Contraddizione__: se è sempre $False$ con ogni possibile __modello__ ovvero $\forall m \not \in M(\alpha)$
- **Soddisfacibile**: se esiste almeno un **modello** in cui $\alpha=True$, ovvero $\exists m \in M(\alpha)$
- **Insodisfacibile**: se NON esiste nessun **modello** in cui $\alpha=True$, ovvero $\forall m \not \in M(\alpha)$ uguale alla contraddizione.

Esiste un legame diretto tra **validità** e **soddisfacibilità**: un enunciato $\alpha$ è **Tautologia** se e solo se $\neg \alpha$ non è **soddisfacibile**. Analogamente, $\alpha$ è **soddisfacibile** se e solo se $\neg \alpha$ non è **tautologia**.

Dati due **enunciati** $\alpha$ e $\beta$ questi sono detti **logicamente equivalenti** indicato con $\alpha \equiv \beta$, se risultano $True$ nello stesso insieme di **modelli**. L'equivalenza logica può essere definita anche in termini di **[[Conseguenza Logica (Deduzione)|conseguenza logica reciproca]]**: due frasi $\alpha$ e $\beta$ sono equivalenti se e solo se $\alpha \models \beta$ e $\beta \models \alpha$.



Tramite l'utilizzo di un [[Linguaggi formali|linguaggio formale]] per la **logica** si possono costruire **preposizioni complesse** combinando le **proposizioni elementari** con **connettivi logici**. ogni connettivo è un [[Operazioni con sottospazi|operatore]] che accetta **valori di verità** e restituisce **valori di verità**. Alcuni esempi di **[[linguaggi formali|linguaggi formali]]** sono:
- [[Logica proposizionale|Calcolo proposizionale]] si limita all'analisi delle combinazioni tra proposizioni atomiche tramite connettivi
- [[Logica del primo ordine (FOL)|logica del prim ordine]] introduce variabili, quantificatori e relazioni, consentendo di esprimere proprietà più generali e strutture complesse.




