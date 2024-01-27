---
type: nota
course: Intelligenza Artificiale
topic: 
tags:
  - IA
Parent MOC: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
---

# AI - Ricerca locale
---
questa classi di ricerca si puo utilizzare sotto le seguenti  assunzioni che
1.  La sequenza di azioni non è importante: quello che conta è unicamente lo stato _goal_
2. tutti gli elementi della soluzione sono nello stato ma alcuni vincolo sono violato 
	1. e.s.  problema delle regine regine: ci sono tutte le regine negli stati non goal il vincolo delle regine che non si attaccano non è rispettato
in generale non ci interessa il path per la soluzione ma solo la soluzione stessa

sul [[AI - Definizione di problemi-Ambienti|Ambiente]]  le assunzioni 
  _Statico_ | _Parzialmente Osservabile_ | _Continuo_ | _Non Deterministico_ | _Sconosciuto_
            


## Proprietà degli algoritmi
- Non sistematici
- tengono traccia solo del nodo corrente e si spostano su nodi adiacente
- non tengono traccia dei cammini (siccome questo non ci interessa)
	1. più efficienti in memoria
	2. possono trovate soluzioni ragionevoli anche in spazzi molto grandi e infiniti (continui)
- soprattutto utili per risolvere problemi di _ottimizzazione_ 
	- lo stato migliore secondo una funzione obiettivo
	- lo stato di costo _minore_

possiamo immaginare  gli stati come una posizione su una superficie
![[AD146924-2EF7-412E-BB56-55D16B4F89AD.jpeg]]
- Un algoritmo lavora muovendosi su questa superficie con l obiettivo di trovare l avvallamento piu basso o il picco piu alto.
- questa è una analogia 2D ma ovviamente funziona per tutte le dimensioni 


### Algoritmi
- [[AI - Ricerca Hill Climbing]]
- [[AI - Ricerca Tempra simulata]]
- [[AI - Ricerca Local beam per]]
- [[AI - Ricerca Generativa-Evolutiva]]