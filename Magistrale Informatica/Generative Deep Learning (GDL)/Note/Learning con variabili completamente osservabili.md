---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Learning con variabili completamente osservabili
---
Il **learning con variabili completamente osservabili** e il caso in cui tutte le variabili del modello compaiono nel training set, quindi non sono presenti [[Latent or hidden Model|variabili latenti]] da inferire durante l'apprendimento. In questa situazione la stima dei parametri e particolarmente semplice, perche le quantita necessarie possono essere ricavate direttamente dalle frequenze empiriche.

Nel caso di [[Maximum likelihood learning]], l'apprendimento si riduce spesso a contare quante volte compaiono certi eventi o certe configurazioni delle variabili e a normalizzare tali conteggi per ottenere probabilita valide.

Questo regime presenta alcune proprieta rilevanti:
- non richiede inferenza su variabili nascoste
- la likelihood e direttamente calcolabile sui dati osservati
- le stime hanno spesso una forma chiusa
- il problema e il punto di partenza naturale per introdurre casi piu complessi

Quando invece alcune variabili del modello non sono osservate, la likelihood osservata contiene marginalizzazioni interne e il learning non puo piu essere ricondotto a un semplice conteggio di frequenze.
