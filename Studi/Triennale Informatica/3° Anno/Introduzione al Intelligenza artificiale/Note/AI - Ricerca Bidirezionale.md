---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca Bidirezionale
---
è un [[AI - Algoritmi di ricerca|Algoritmo di ricerca]] applicabile in cui  

- ricerca in avanti o guidata dai dati:
	si esplora lo spazio di ricerca dallo stato iniziale allo stato obiettivo; 
- ricerca all’indietro o guidata dall’obiettivo: 
	- si esplora lo spazio di ricerca a partire da uno stato goal e riconducendosi a sotto-goal fino a trovare uno stato iniziale.

si basa sul idea che se si è trovata una soluzione allora c è un intersezione tra le due esplorazioni 
![[Pasted image 20230212023837.png]]

### Applicabilità
_sotto condizioni_ quali:
- Si può definire facilmente uno stato finale o più stati finali eventualmente connessi ad uno stato finale "dummy"
	- Concetti astratti come l obiettivo del [[problema delle 8 regine]] rende questa strategia inapplicabile
- si può generare lo stato predecessore di uno stato 
	- facile quando tutte le azioni sono reversibili (predecessore = successore)

### Analisi
[[Complessita]]
- _Strategia  completa_ se si esplora con [[AI - Ricerca in ampiezza BF|BF]]
- _Strategia  ottimale_
-  _Complessità nel tempo_  $O(b^{d/2})$
	- il consto totale $b^{d/2} +b^{d/2}$ 
- _Complessità spazio_ (nodi in memoria): $O(b^{d/2})$ _Cammino dalla radice goal_ + _cammino da goal a radice_ 