---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
  - ML
---

# Overfitting e Underfitting
---
__Overfitting__ e __Underfitting__ sono due concetto del [[Concetti generali del Machine Learning|ML]] che mettono il relazione la __complessità__ del modello usato e i dati utilizzati per il training 

## Overfitting
un learner è in  __overfitting__ se genera un ipotesi $h \in H$  tale che ne esiste un altra  $h' \in H$ che ha _[[Statistical Learning Theory (SLT)|Errore empirico]]_ $R_{emp}$ maggiore sui dati di training e un __errore di generalizzazione__ $R$ più basso

## Underfitting 
un learner è in  __underfitting__ se genera un ipotesi $h \in H$ tale che  ne esiste un altra  $h' \in H$ che ha _[[Statistical Learning Theory (SLT)|errore empirico]]_ $R_{emp}$ più basso sui dati di training e un _errore_ $R$ piu basso

#### Combattere overfitting e underfitting
per la gestione della complessità di un [[Definizione di Modello di Machine Learning|modello]] si utilizza la [[Statistical Learning Theory (SLT)|statistical learning theory]] 