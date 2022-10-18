---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Analisi del errore
---
Analizzando un fenomeno del mondo reale se ne crea il **modello matematico continuo** questo può ci permette di rovarne le proprietà qualitative(esistenza, unicia, regolarita, ecc.)questo pero non ci permette di soluzione una soluzione concreta al problema di consequenza il modello viene aprossimato prendendo solo alcuni suoi punti quindi creando un **modello matematico  discreto**

![[Raccolta UniPi INF/Note/2° Anno/Calcolo Numerico(CN)/Media/Untitled 1.png]]

non tutti i numeri sono rapresentabili con dei valori finiti per esempio $\pi$ o $\sqrt{2}$ ma noi possimo solo calcolare con un aritmetica finita che aprossima la soluzione reale, questo introduce alcuni errori

## Errori

- Errore di rapresentazione: generati dall impisibilita di tenere traccia di numeri con infinite cifre
- Errore  delle operazioni: generati dalle operazioni su numeri finiti
- Errore inerente: tutto l errore di rapresentazione propagato nella soluzione
- Errore algoritmico: tutto l errore delle opoerazioni propagato nella soluzione

## Algoritmi

i pasi di calcolo quindi gli algoritmi possono essere definiti in due modi

- Numericamente instabili: ovvero quelli in cui si presenta un elevata propagazione dell errore
- Numericamente stabili: ovvero quelli in NON cui si presenta un elevata propagazione dell errore

in generale è defficile stabilire se un algoritmo è stabile o instabile

---


