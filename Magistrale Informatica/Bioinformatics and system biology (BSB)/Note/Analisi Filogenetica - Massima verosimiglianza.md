---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi Filogenetica - Massima verosimiglianza
---
L’**Massima verosimiglianza per l [[Analisi Filogenetica|analisi filogenetica]]** è un approccio  che ricostruisce alberi evolutivi selezionando la topologia che rende più probabile l’osservazione dei dati sperimentali, dato un modello esplicito di evoluzione molecolare. Scelto in base alla probabilità complessiva che le sequenze osservate siano state generate lungo quella struttura.

La massima verosimiglianza assume che i cambiamenti nei caratteri biologici seguano un processo statistico descritto da un modello di sostituzione, nel quale ogni mutazione ha una certa probabilità di verificarsi lungo i rami. L’obiettivo è quindi determinare l’albero $T$ e i parametri del modello che massimizzano la [[Definizione di Probabilita|probabilità]] dei dati $D$:$$L(T)=P(D \mid T, M)$$dove $M$ rappresenta il modello evolutivo adottato. La qualità di un albero viene valutata attraverso la funzione di verosimiglianza, calcolata combinando le probabilità di sostituzione lungo ciascun ramo per tutte le posizioni informative dell’allineamento.

Il metodo opera tipicamente a partire da un [[Allineamento di sequenze multiple (MSA)|allineamento di sequenze multiplo]] , da cui deriva un insieme di caratteri omologhi. Per ogni possibile topologia viene stimato il valore di verosimiglianza, includendo anche la lunghezza dei rami, che rappresenta la quantità attesa di cambiamenti evolutivi è un problema [[Classi di complessita - NP-Hard|NP-hard]]

Poiché lo spazio delle topologie cresce rapidamente con il numero di sequenze, la ricerca dell’albero ottimale non viene eseguita mediante enumerazione completa, ma attraverso algoritmi euristici che esplorano progressivamente le configurazioni più promettenti. In questo contesto, la valutazione probabilistica permette di confrontare alberi alternativi anche quando richiedono numeri diversi di mutazioni, poiché il criterio è basato sulla plausibilità statistica e non sull’economia evolutiva.