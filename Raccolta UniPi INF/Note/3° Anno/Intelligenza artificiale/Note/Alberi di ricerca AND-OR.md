---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Alberi di ricerca AND-OR
---
si utilizzano in [[Definizione di problemi per AI - Ambienti|ambienti]] più realistici dove questo è parzialmente osservabile e non deterministico.

gli [[Agenti Razionali|agenti]] in questo caso elabora una “Strategia” che tiene conto delle diverse eventualità, queste scoperte con delle percezioni sul ambiente. l agente sviluppa un _piano con contingenza_ 

## Alberi di ricerca AND-OR
è un [[Albero struttura dati|albero]] di cui 
- I nodi _OR_ sono le _scelte del agente_, un unica azione
- i nodi _AND_ sono le _diverse contingenze_ ovvero al esecuzione del azione si presentano i vari stati possibili, e sono tutte da considerare
una soluzione a un problema di ricerca _AND-OR_ è un albero che 
- ha un nodo obiettivo in ogni foglia
- specifica un unica azione nei nodi OR
- include tutti gli archi uscenti da nodi AND
![[E704A1ED-2715-4625-8810-609F9323BCE1.jpeg]]