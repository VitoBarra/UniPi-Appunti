---
Subject: Intelligenza Artificiale
topic: nota
tags: IA
---

Prev: [[Introduzione al Intelligenza Artificiale (IIA)]]

# Risoluzione SLD
---
è un [[AI - Sistemi di deduzione (o di Inferenza)|Sistema di deduzione]]  utilizzato dal [[AI - Agenti logici - Sistemi a regole]] 
- La risoluzione SLD(Selection linear Definite-clauses) è una strategia ordinata
- la risoluzione SLD è completa per clausole Horn
- A partire da un programma P e da un goal G si costruisce l albero di risoluzione 

### Albero di risoluzione SLD
dato un programma logico P, l albero SLD per un G è Dfinito come segue:
- ogni nodo dell albero corrisponde a un goal 
- la radice è $:- G_1,G_2,\dots G_k$ il goal di partenza
- Sia $:- G_1,G_2,\dots G_k$ un nodo dell albero; il nodo ha tanti discendenti quanti sono i fatti e le regole in $P$ la cui testa è unificabile con $G_1$
- Se $A :- B_1,\dots,B_k$ e $A$ è unificabile con $G_1$ con $\gamma = MGU(A,G_1)$ un discendente è il goal $:-(B_1,\dots,B_k,G_2,\dots,G_k)\gamma$
- i nodi che sono clausole vuote sono _successi_
- i nodi che non hanno successori sono _fallimenti_
	 


- La strategia è completa per clausoleo Horn definite
	- Se $P \cup \{\lnot G\}$ è insoddisfacibile, allora una delle foglie deve essere la clausola vuota (successo)
- non è restrittivo andare in ordine nel risolvere i sotto al in and 
- la sostituzione corrisponde è la risposta calcolata
- la _completezza_ dipende dalla strategia di esplorazione del alboero
	- Prolog Utilizza una discesa in profondità con backtracking in caso di fallimento
		- Strategia _non completa_
			- puo finire in cicli a seconda dell applicazione delle regole 