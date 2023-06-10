---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# TV-Consegue algoritmo per SAT
---
una algoritmo per fare [[Problema della Sodisfacibilita (SAT)|model checking]] e serve a scromprire se una data $\alpha$ e [[Base di conoscenza (KB)#Conseguenza logica|conseguenza logica]] di $KB$ nel contesto del utilizzo di [[Agenti Logici - Calcolo proposizionale|Agenti con calcolo proposizionale]]

Enumera tutte le proprieta interpretazione di KB
- con $k$ simboli, $2^k$ possibili interpretazioni, quindi molto lento
- Per _ciascuna_ [[Logica proposizionale#Interpretazione|interpretazione]] si ha che
	- Se l _interpretazione_ è modello di $KB$ allora si controlla che sia anche modello di $\alpha$
	- se non soddisfa $KB$ si va avanti
- Se si trova anche una sola interpretazione che soddisfa $KB$ ma non $\alpha$ allora $\alpha$ non è conseguenza logica


### Pseudo codice
```python

```