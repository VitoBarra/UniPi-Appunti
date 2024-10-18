---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Concept Learning
---
L’ apprendimento di _concetti_ è formalizzato come 
- miglioramento sul _task_ $T$
- guardando la _performance_ $P$
- basato sul _esperienza_ $E$


Si tratta di  


## Definizioni

#### Concept learning
_Concept Learning_: capacita di inferire una funzione _booleana_ da esempi negativi e positivi. 
#### dati d Esempio per la Classificazione
- definitivo come $<input,output> \rightarrow <x,c(x)>$ 
	- dove $c(x)$ è una funzione booleana che va da $X \rightarrow \{t,f\}$
		- $X$ è lo spazio delle istanze
	- è un caso specifico di $<x,d>$
#### Soddisfa
- una _Ipotesi_ $h(x)$ si diche che _soddisfa_ x se $h(x)=1$
#### Consistenza del ipotesi
- Un _ipotesi_ h(x) è consistente con
	- _un esempio_  se $h(x) =c(x)$
	-  con un insieme di dati $D$ se lo è per tutti  i dati d esempio in $D$



![[004017FB-293F-4B89-9116-D53645BD3CB0.jpeg]]

- in generale la cardinalità di $|H| = 2^{\#\text{-instances}}= 2^{2^{n}}$ per input binari $n =$ _input dimension_



Per avere una ricerca efficiente  si restringe lo spazio delle ipotesi ad una sotto insieme molto più piccolo dello spazio delle soluzioni. si aggiunge quindi un _[[Bias Induttivo|Bias]]_ che fare questa restrizione.
alcuni esempi di queste restrizioni sono 
- Le funzioni in forma [[Forma normale congiuntiva (CNF)|congiuntiva]] usati nel [[Concept learning - Candidate elimination|candidate elimination]] e nel [[Concept learning - Find-S|Find-S]]
- le espressioni lineari come nel [[Modelli lineari (LMS)|modello lineare]]


Parlando del caso delle regolo congiuntive la cardinalita dello spzio delle ipotesi $H$ è
- con solo _letterali positivi_:  $|H|= 2^n$
- includendo i letterali negati $|H| = 3^n+1$


### Ipotesi di apprendimento induttivo
assunzione che si fa.
- ogni ipotesi $H$ che approssima la funzione _target_ sui dati di training approssimerà anche i valori della funzione _target_ su dati non ancora visti.

quindi si ha che 
- $h(x)=c(x)$ for all $x$ in $D$ (ovvero è _consistente_ con $D$) $\implies$
- $h(x) = c(x)$ for all $x$ in $X$ 


##### Definizione di consistenza
dato 
- $D$ un insieme di dati di esempi
- dove $c : X \rightarrow \{0,1\}$ è una funzione
si dice consistente 
$$Consistent(h,D):= \forall <\boldsymbol x,c(\boldsymbol x)> \in D \ \ \ .   h(\boldsymbol x)=c(\boldsymbol x)$$  

### Ordine parziale Dal genere al allo specifico 
dato una ipotesi $h_j$ è un altra ipotesi $h_k$ definite su $X$. allora $h_j$ è _piu generale o uguale_ di $h_k$  $\iff \forall x \in X : [(h_k(x)=1) \rightarrow (h_j(x)=1)]$
- le relazione $\geq$ impone un [[Ordinamenti|oridnamento parziale]] sullo spazio delle ipotesi 
- possiamo utilizzare questo ordinamento per realizzare algoritmi più efficienti. 
 





