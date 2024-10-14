---
Subject: Intelligenza Artificiale
topic: nota
tags: IA
---

Prev: [[Introduzione al Intelligenza Artificiale (IIA)]]

# Algoritmo DPLL per SAT
---
una algoritmo per fare [[Problema della Soddisfacibilita (SAT)|model checking]] e serve a scoprire se una data $\alpha$ e [[AI - Base di conoscenza (KB)#Conseguenza logica| conseguenza logica]] di $KB$ nel contesto del utilizzo di [[AI - Agenti Logici - Calcolo proposizionale|Agenti con calcolo proposizionale]]

## Eurisitche utilizate

### Terminazione anticipata
- Si puo decidere sulla verità di una clausola anche con interpretazione parziali: basta che un letterale sia vero
	- Se A è vero alo sono anche $\{A,B\}$ e $\{A,C\}$ indipendentemente dal valore di $B$ o $C$
- Se anche una sola clausola è falsa l interpretazione non può essere un modello dell insieme di clausole.

### Simboli puri
_Simbolo puri_: è un letterale che compare sempre con lo stesso segno in tutte le clausole. (es in tutte le clausole compare sempre non negato o sempre negato)
- Nel determinare se un simbolo è pure se ne possono trascurare le occorrenze in clausole gia rese vere
- I _simboli puri_ possono essere assegnati a 
	- $True$ se il letterale è normale  
	- $False$ se è negato
- Questo siccome a noi interessa trovare un modello 
- _Non_ si eliminano _modelli utili_: se le clausole hanno un modello continuano ad averlo dopo questo asssegname not (non renderà mai falsa una clausola in cui compare il simbolo puro)


### Clausole unitarie
_clausole unitaria_: una clausola con un sono letterale _NON assegnato_
- $\{B\}$ è una clausola unitaria 
- $\{B,\lnot C\}$ se $C = true$
 conviene assegnare priva i valori al letterale in clausole unitari, siccome stiamo cercando un modello le clausole unitarie sono _assegnamenti obbligati_ dal fatto che dobbiamo rendere vera la clausola. abbiamo quindi che 
- $\{A\}$ allora $A=true$
-  $\{\lnot A\}$ allora $A=false$


### Pseudo codice
```python

```



## Ulteriori ottimizzazioni (non approfondito) 
- Analisi di completi, si uno suddividere il problema in sotto problemi indipendenti se le variabili possono essere suddivise in sotto insiemi disgiunti (_senza simboli in comune_)
- Ordinamento di variabili e valori: scegliere la varibiale che compare in piu clausole
- backtracking intelligente