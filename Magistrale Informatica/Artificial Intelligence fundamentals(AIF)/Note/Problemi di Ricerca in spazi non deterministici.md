---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca in spazi non deterministici
---
In [[Definizione di Problemi-Ambienti|ambienti non deterministici]], la stessa azione nello stesso stato puo risultare in piu stati possibili. Un [[Agenti Razionali|agente razionale]] situato un ambiente di questo tipo per fare [[Problemi di ricerca|ricerca]] non può ragionare in termini di stati singoli, ma deve considerare un insiemi di **stati possibili**.

Tale insieme viene rappresentato attraverso uno ***stato di credenza*** (***belief state***), che riflette tutte le configurazioni che l’agente considera **plausibili**. Di conseguenza, la **soluzione** alla ricerca deve essere strutturata come un ***piano condizionale*** (**contingent solution**), in cui le azioni da intraprendere **dipendono dai percetti** che l'agente riceve durante l’esecuzione del piano. Un **piano condizionale** ha quindi la forma di un [[Albero di decisione|albero decisionale]], le cui diramazioni corrispondono a possibili evoluzioni del processo decisionale in presenza di incertezza.

Per modellare formalmente l’evoluzione degli stati in **ambienti non deterministici**, si generalizza la **funzione di transizione** $T$ della [[Problemi di ricerca|ricerca]] in modo da considerare tutti gli stati possibili:$$
T : S \times A \rightarrow S^n
$$dove $S$ è l’insieme degli stati e $A$ l’insieme delle azioni. Questa funzione descrive tutti i possibili esiti di un’azione in un dato stato.
