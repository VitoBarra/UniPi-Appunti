---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Problema Sequence Assembly
---
Il problema **Sequence Assembly** deriva dalla necessità di assemblare le sequenze ottenute tramite le [[Tecnologie di sequenziamento|tecnologie di sequenziamento]], che sono spesso più corte della sequenza di interesse. È quindi necessario **dedurre** la sequenza finale a partire da questi frammenti. A tal fine si utilizzano più sequenze parzialmente sovrapposte, che devono essere integrate per ricostruire la sequenza completa.

La sovrapposizione delle sequenze consente di individuare eventuali errori nelle singole letture: il confronto tra le letture ridondanti permette infatti di ottenere un consenso attendibile della sequenza reale, aumentando la **precisione** del sequenziamento.
![[IMG - allineamento di sequenze.png]]
Una delle problematiche del **Sequence Assembly** è la possibile unione errata di due sequenze identiche che, pur essendo uguali, sono in realtà presenti in regioni differenti del [[DNA Struttura e funzionalità|DNA]]. In questi casi le letture corrispondono a porzioni distinte della sequenza di interesse, ma risultano indistinguibili dal punto di vista del contenuto nucleotidico, rendendo quindi difficile stabilire la loro corretta posizione nell’assemblaggio.
![[IMG - problema delle sequenze ripetute nel assemblamento di sequenze.png]]
