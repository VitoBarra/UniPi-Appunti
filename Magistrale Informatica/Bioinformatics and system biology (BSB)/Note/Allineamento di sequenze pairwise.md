---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze pairwise
---
L’**allineamento di sequenze pairwise** è un tipo di [[Allineamento di sequenze]] in cui il confronto è limitato a **due sequenze**. Esso rappresenta il caso elementare del problema di allineamento e costituisce la base concettuale per estensioni più complesse, come l’[[Allineamento di sequenze multiple (MSA)|allineamento multiplo]]. Il pairwise alignment introduce una **corrispondenza esplicita** tra le posizioni delle due sequenze.

L’insieme delle soluzioni ammissibili è costituito da tutte le disposizioni relative delle due sequenze che preservano l’ordine dei simboli. La restrizione a due sequenze rende il problema concettualmente più semplice e consente di definire in modo esplicito lo **spazio delle soluzioni**, che cresce rapidamente con la lunghezza delle sequenze ma rimane strutturato in modo tale da poter essere esplorato sistematicamente.

il **pairwise alignment** è formulato come [[Problemi di ottimizzazione|problema di ottimizazione]] è la **funzione obiettivo elementare** piu semplice e libera dal contesto che si puo usare conta le corrispondenze tra simboli e una penalità costante alle operazioni di inserzione, cancellazione o sostituzione. In questa formulazione, l’allineamento ottimale è quello che **minimizza il numero totale di operazioni** necessarie per trasformare una sequenza nell’altra, oppure, in modo equivalente, che **massimizza il numero di corrispondenze**.
![[IMG - Allineamento di sequenze pairwise senza gap.png]]
![[IMG - Allineamento di sequenze pairwise con gap.png]]


