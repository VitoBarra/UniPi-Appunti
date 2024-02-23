---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---


# TV-Consegue algoritmo per SAT
---
una algoritmo per fare [[Problema della Soddisfacibilita (SAT)|model checking]] e serve a scoprire se una data $\alpha$ e [[AI - Base di conoscenza (KB)#Conseguenza logica|conseguenza logica]] di $KB$ nel contesto del utilizzo di [[AI - Agenti Logici - Calcolo proposizionale|Agenti con calcolo proposizionale]]

Enumera tutte le proprieta interpretazione di KB
- con $k$ simboli, $2^k$ possibili interpretazioni, quindi molto lento
- Per _ciascuna_ [[Logica proposizionale#Interpretazione|interpretazione]] si ha che
	- Se l _interpretazione_ è modello di $KB$ allora si controlla che sia anche modello di $\alpha$
	- se non soddisfa $KB$ si va avanti
- Se si trova anche una sola interpretazione che soddisfa $KB$ ma non $\alpha$ allora $\alpha$ non è conseguenza logica


### Pseudo codice
```python

```