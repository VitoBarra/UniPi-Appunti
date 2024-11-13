---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Find-S
---
__Find-S__ è un algoritmo di [[Concetti generali del Machine Learning| Machine learning]] per il [[Concept Learning|concept learning]] che utilizza l ordinamento parziale costruibile sullo spazio delle ipotesi 


### Ipotesi
- Lo spazio delle ipotesi è ristretto a ciò che è esprimibile in [[Forma normale congiuntiva (CNF)|forma normale congiuntiva]]
- i dati di training non sono _mai_ perturbati


## Algoritmo 
1. inizializza $h$  alla ipotesi più specifica
2. per ogni _positive_ training istanza $x$
	1. __per ogni__ attributo $a_i$ in $h$
	2. __if__ $a_i$ NON è soddisfatto in $h$ da $x$
	3. __then__  sostituisce $a_i$ in $h$ dal prossimo vincolo più generale che è soddisfatto da $x$ 
3. Output del ipotesi $h$



### Proprietà
- ipotesi della rappresentazione come [[Forma normale congiuntiva (CNF)|forme congiuntiva]] 
	- è il suo bias che limita l espressività del modello
	- è una forte limitazione 
- da in output l ipotesi più _specifica_ con $h$ _consistente_ con gli esempi positivi
- l ipotesi $h$ sarà anche consistente con i casi _negativi_ del training set se il concetto è contenuto in $H$
	- perché $c \geq h$ ovvero c è poi generale


### Problematiche
- non si può dire nulla sul fatto che l algoritmo converge verso una soluzione. ovvero non si può dire nulla sul unicità del ipotesi consistente con gli esempi i training 
- non dice nulla sul inconsistenza dei dati, questo siccome ignora i casi _negativi_: non accetta dati perturbati