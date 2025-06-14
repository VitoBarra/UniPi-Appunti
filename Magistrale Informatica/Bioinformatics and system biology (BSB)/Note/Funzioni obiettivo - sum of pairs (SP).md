---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Funzioni obiettivo - sum-of-pairs (SP)
---
La **sum-of-pairs (SP)** è una **funzione obiettivo** utilizzata nell’[[Analisi di sequenze|Analisi di sequenze]] e, in particolare, nei problemi di [[Allineamento di sequenze multiple (MSA)|Allineamento di sequenze multiple]], nei quali la costruzione di un allineamento viene formulata come un [[Problemi di ottimizzazione|problema di ottimizzazione]]. La funzione **SP** assegna un punteggio a un allineamento multiplo sulla base dei contributi derivanti dai [[Allineamento di sequenze pairwise|confronti pairwise]] indotti dall’allineamento stesso.

Formalmente, sia $M$ un allineamento multiplo di $n$ sequenze, e sia $M_{i,c}$ il simbolo (o gap) della $i$-esima sequenza nella colonna $c$. Indicata con $s(\cdot,\cdot)$ una funzione di punteggio che include sia i confronti simbolo–simbolo sia le penalità di gap, la funzione **sum-of-pairs** è definita come: testo $$SP(M)=\sum_{c}\;\sum_{1\le i<j\le n} s\bigl(M_{i,c},\,M_{j,c}\bigr)$$ testo

Per ogni colonna dell’allineamento il numero di confronti pairwise è dato dalla [[Formula di gauss|formula di Gauss]] ed è pari a $\cfrac{n(n-1)}{2}$. Ne segue che il costo computazionale per il calcolo del valore **SP(M)** di un **MSA fissato** con $C$ colonne è proporzionale a $C\cdot \cfrac{n(n-1)}{2}$.