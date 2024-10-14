---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Ricerca Generativa-Evolutiva
---
è un algoritmo di [[AI - Ricerca locale|Ricerca locale]] e sono varianti della [[AI - Ricerca Local beam per#Versione stocastica|Beam serch stocastica]] in cui gli stati successori sono ottenuti combinando due stati genitori:


- Popolazione iniziale:
	- k stati/individui generati casualmente
	- ogni individuo è rappresentato come una stinga
- Gli individui sono valutati da una _funzione di fitness_

  - Si selezionano gli individui per gli “accoppiamenti“ con una probabilità proporzionale alla _fitness_
  - Le coppie danno vita alla _generazione_ successiva
	  - Combinando materiale genetico ( crossover)
	  - Con un meccanismo aggiuntivo di mutazione genetica (casuale)
  - La popolazione ottenuta dovrebbe essere migliore
  - La cosa si ripete fino ad ottenere stati abbastanza buoni (stati obiettivo) o finche non miglioriamo più
 ![[F2E62E30-CD41-4334-9715-8450201E831E.jpeg]]
- Per ogni viene coppia (scelta con probabilita proporzionale alla fitness) viene scelto un punto di crossing over e vengono generati due fili scambiando si pezzi
-  Viene infini effettuata una mutazione casuale che da luogo alla prossima generazione e
- la fitness progressivamente tenderà a favorire generazioni migliori
- emula i meccanismi genetici ma anche l evoluzione della spece



#### Vantaggi
-  Tendenza a salire della beam search stocastica
- interscambio info tra thread paralleli di riceca 
- funzione meglio se il problema ha componenti significative rappresentati in sottostringhe 
- _Punto critico_: rappresentare il problema in stringhe 
