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
il **Planning Classico** è definito come il compito di individuare una **sequenza di azioni** per raggiungere un obiettivo in un ambiente **discreto**, **deterministico**, **statico e completamente osservabile**, questo per essere fatto anche con[[Problem-Solving Agent| agenti per fare problem solving]] e [[Agenti Knowledge Based|agente logico ibrido]] ma entrambi presentano due limitazioni:
- richiedono euristiche ad hoc per ciascun dominio 
- necessitano di rappresentare esplicitamente uno spazio di stati esponenzialmente grande.
Per superare queste limitazioni, si puo usare una [[Rappresentazione del ambiente|factored rapresentation]] chiamata **[[Planning - Planning Domain Definition Language (PDDL)|Planning Domain Definition Language (PDDL)]]**, questa rappresentazione è basta sulla [[Logica del primo ordine (FOL)|logica del promo ordine]] ed è in grado di descrivere molte **azioni possibili** con un unico **schema di azione** senza conoscenze specifiche del dominio. 
il **PDDL** di base gestisce domini di **pianificazione classici**, mentre le estensioni supportano domini non classici ovvero, [[Definizione di Problemi-Ambienti|continui, parzialmente osservabili, concorrenti e multi-agente]]. 