---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IIA
---

# Concept learning - Candidate elimination
---
il __Candidate elimination__ è un [[Algoritmi di learning supervisionato|algoritmo supervisionato]] per [[Concetti generali del Machine Learning|Machine learning ]] per il [[Concept Learning|Concept learning]] per la ricerca del __version space__.
Sfrutta il teorema di bound del __version space__ crearlo __iterativamente__ .

## Algoritmo Candidate elimination
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



### proprieta
Il __Version Space__ trovato convergerà verso l'ipotesi che descrive correttamente il concetto target solo se:  
1. non ci sono errori negli esempi di addestramento  
2. esiste un'ipotesi $h\in H$ che descrive correttamente il concetto target.  

Se il Version Space converge a un'ipotesi significa che G e S convergono entrambe alla stessa ipotesi.  
Se ci sono errori negli esempi di addestramento, il Version Space sarà vuoto.  