---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Candidate elimination
---
_Candidate elimination_ e' un algoritmo per [[Machine Learning|Machine learning ]] per il [[ML - Concept Learning|Concept learning]]

## Definizioni
- _Version Space_: $VS_{H,D}$ in accordo con lo spazio delle ipotesi $H$ è il training set D,  è il sotto [[Insiemi Matematici|insieme]] di ipotesi consistenti con tutte i dati di training $$VS_{H,D} = \{h\in H | consistent(h,D)\}$$
- dove per definire $consistent$ si utilizza al definizione di consistenza ![[ML - Concept Learning#Definizione di consistenza]]
 
### Algoritmi per calcolo di Version space
#### lista e elimina
1. VersionSpace $\leftarrow$ lista di tutte le possibili ipotesi
2. __per ogni__ training example $<x,c(x)>$
	1. Rimuovi da VersionSpace ogni ipotesi inconsistente 
3. output di VersionSpace

questo algoritmo è irrealistico, richiederebbe di enumerare tutte le ipotesi 



## Rappresentazione del Version Spaces
- _general boundary_: denominato _G_ è l insieme degli elementi massimamente generalizzati delle ipotesi $H$ consistenti con i training data $D$
- _Specific boundary_: denominato _S_ è l insieme degli elementi più specifici delle ipotesi $H$ consistenti con i training data $D$

#### Teorema
ogni membro del _version space_ si trova tra _G_ e _S_
$$VS_{H,D}= \{h\in H|(\exists s \in S)(\exists g \in G)(g \geq h \geq s)\}$$


## Algoritmo del eliminazione dei candidati 
1. $G \leftarrow$ ipotesi più generale in $H$
2. $S \leftarrow$ ipotesi più specifica in $H$
3. __per ogni__ training example $d$ 
	1. __Se__ $d$ é un esempio positivo 
		1. _rimuovi_ da $G$ ogni ipotesi che è inconsistente con $d$
		2. __per ogni__ ipotesi $s \in S$ che  non è consistente con $d$ 
		3. Generalizza $S$
			1. rimuovi $s$ da $S$
			2. aggiungi ad $S$ tutte le _minime_ generalizzazioni $h$ di $s$ tale che
				- $h$ sia consistente con $d$
				- alcuni membri di $G$ siano _più generali_ di $h$
			3. rimuovi da $S$ tutte le ipotesi che sono _più_ generali di un altra ipotesi in $S$
				- da capire come confrontarle
	2. __else__ se $d$ è un esempio negativo  
		1. rimuovi da $S$ ogni ipotesi che è inconsistente con $d$
		2. __per ogni__ ipotesi $g \in G$ che  non è consistente con $d$ 
		3. Specializza $G$
			1. rimuovi $g$ da $G$
			2. aggiungi ad $g$ tutte le _minime_ specializzazioni $h$ di $g$ tale che
				- $h$ sia consistente con $d$
				- alcuni membri di $S$ siano _più specifici_ di $h$
			3. rimuovi da $G$ tutte le ipotesi che sono _meno_ generali di un altra ipotesi in $G$
				- da capire come confrontarle