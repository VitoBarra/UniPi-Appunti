---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca Tempra simulata
---
è un algoritmo di [[Ricerca locale|Ricerca locale]] Scelta [[Definizione di Probabilità|stocastica]] ma non del tutto casuale perché poco efficiente


ad ogni passi si sceglie un successore $n’$ a caso:
- Se migliora lo stato corrente si passa a quello stato
- altrimenti quel nodo viene scelto con [[Definizione di Probabilità|probabilita]] $p = e^{\Delta E/T}$
	- dove $\Delta E = f(n’)-f(n)$ e $T$ è un parametro detto _temperatura_ che decresce seguendo un piano definito (anche esso parametro) con il _progredire temporalmente_  del algoritmo
	- Cosi facendo la $p$ è inversamente proporzionale al peggioramento, se $\Delta E$ è un numero molto alto negativo $p$ si abbassa



## Analisi
- la probabilità  $p$ di decrescere diminuisce con il tempo avvicinandosi sempre di piu al comportamento di [[Ricerca Hill Climbing|Hill climbing]]
- se $T$ viene decrementato abbastanza lentamente con probabilità tendenze ad 1 si raggiunge la soluzione ottimale 
- Valori per $T$ determinato _sperimentalmente_: valore iniziale di T tale che per valori medi di $\Delta E,p=e^{\Delta E / t}$ sia al in circa $0.5$

