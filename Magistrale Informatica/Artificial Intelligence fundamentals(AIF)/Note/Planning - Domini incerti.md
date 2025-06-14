---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Domini incerti
---
Il [[planning|planning]] può essere esteso al gestire [[Definizione di Problemi-Ambienti|ambienti non deterministici]], [[Definizione di Problemi-Ambienti|parzialmente osservabili]] e [[Definizione di Problemi-Ambienti|sconosciuti]].  
Questa estensione ci porta a dover gestire due principali dimensioni di incertezza:  
1. **Incertezza sullo stato del mondo**, dovuta alla **parziale osservabilità**;  
2. **Incertezza sugli effetti delle azioni**, dovuta al **non determinismo** delle azioni.  
Queste condizioni portano alla necessità di rappresentare l’ambiente non con una singola base di conoscenza, ma con un **belief state**.  
Il **belief state** rappresenta l’insieme di tutti gli stati del mondo nei quali l’agente potrebbe trovarsi, anziché lo stato effettivo del mondo, per poter gestire il **belief state** si utilizza il linguaggio [[Planning - Planning Domain Definition Language (PDDL)|PDDL esteso]] grazie al quale l'**agente pianificatore** puo dare in output un **piano contingente** invece che una sequenza di azioni.


