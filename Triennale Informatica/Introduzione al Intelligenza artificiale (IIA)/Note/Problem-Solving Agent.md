---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---

# Problem-Solving Agent
---
Agli **Agenti risolutori di problemi** sono [[Agenti Razionali|agenti]] che utilizzano una rappresentazione dell’ambiente [[Rappresentazione del ambiente|atomica]] è il loro compito è partire in un dato stato e raggiungere un stato obiettivo. 
Adottano il __paradigma__ dei [[Problemi di ricerca|problemi ricerca]] e quindi per definire un comportamento esplorano uno **spazio di stati** con un [[Algoritmi di ricerca non informati|algoritmo di ricerca]],  fino a raggiungere lo **stato obiettivi**, costruendo una **sequenza di azioni** per ottenere quello stato.
- **Formulazione dell’obiettivo**: l’agente stabilisce quale stato del mondo desidera raggiungere. Gli obiettivi guidano il comportamento limitando lo spazio delle possibili azioni da considerare.
 - **Formulazione del problema**: l’agente costruisce un modello astratto del dominio rilevante, descrivendo gli ***stati*** e le ***azioni*** disponibili. (e.g. citta, spostamenti)
 - **Ricerca**: l’agente simula internamente delle sequenze di azioni nel proprio modello, esplorando lo spazio degli stati alla ricerca di una sequenza che lo conduca allo stato obiettivo.  
 - **Esecuzione**: una volta ottenuta la soluzione, l’agente esegue le azioni una alla volta.

Le strategie per ottenere lo stato obiettivo sono 2:
- **open-loop**: l’agente può ignorare i suoi percezione durante l’esecuzione del piano trovato. Questo applicabile In [[Definizione di Problemi-Ambienti|ambienti noti, deterministici e completamente osservabili]] dove la **soluzione** è una sequenza fissa di azioni
- **closed-loop**: l’agente continua a monitorare i percetti durante l’esecuzione, usata in  [[Definizione di Problemi-Ambienti|ambienti parzialmente osservabili o non deterministici]], dove le azioni da intraprendere potrebbero cambiare a seconda dei cambiamenti del ambiente, serve quindi un piano contingenziale


