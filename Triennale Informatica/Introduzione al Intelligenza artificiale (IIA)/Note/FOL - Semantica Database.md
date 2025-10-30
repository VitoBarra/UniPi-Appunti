---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
---

# Semantica Database per FOL
---
la **Semantica Database** per la [[Logica del primo ordine (FOL)|logica del prima ordine]] è una semantica usata per definire le [[Logica del primo ordine (FOL)#Semantica|interpretazioni]] della **logica del primo ordine** dove valgono le assunzioni: 
- **unique-names** stabilisce che ogni simbolo costante si riferisce a un oggetto distinto.
- **Closed-world** considera false tutte le proposizioni atomiche non esplicitamente dichiarate come vere. 
- **Domain Closure** limita il **dominio degli oggetti** ai soli elementi denotati dai simboli costanti presenti.  
con questa semantica i mondi possibili per connettere due simboli è limitato a differenza della semantica classica dove il numero di possibili mondi è infinito.:![[IMG - Semantica Database per FOL.png]]



### a cosa e' utile
La traduzione del linguaggio naturale in linguaggio logico richiede una formalizzazione accurata delle relazioni tra oggetti e proprietà. Una semplice congiunzione di relazioni del tipo $$
R(a, b) \wedge R(c, b)
$$non è sufficiente a descrivere compiutamente una situazione, poiché non garantisce né la distinzione tra gli elementi coinvolti né la completezza del dominio considerato. Per ottenere una rappresentazione esaustiva, occorre aggiungere vincoli di disuguaglianza tra costanti diverse  $$
a \neq c
$$e un vincolo di universalità che limiti la relazione ai soli oggetti esplicitamente menzionati  $$
\forall x \, (R(x, b) \Rightarrow (x = a \vee x = c)).
$$Questa formulazione, più articolata rispetto alla corrispondente proposizione in linguaggio naturale, assicura la precisione semantica necessaria per l’inferenza logica corretta.  

usando la **semantica database** una formula del tipo  $$
R(a, b) \wedge R(c, b)
$$viene interpretata come completamente descrittiva del fenomeno, implicando che solo gli oggetti nominati partecipano alla relazione. Il numero di modelli possibili risulta pertanto finito, in contrasto con la molteplicità indefinita prevista dalla semantica standard del primo ordine.  

La scelta della semantica dipende dal grado di conoscenza del dominio e dall’obiettivo rappresentativo: la semantica dei database privilegia la completezza e la certezza dei dati, mentre la semantica standard mantiene maggiore generalità, a costo di formulazioni più complesse e meno dirette.