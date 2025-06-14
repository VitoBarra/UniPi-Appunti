---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Proportional distance (p-distance)
---
**Proportional distance** o **p-distance** è una [[Definizione di distanza|distanza]] tra due [[Stringhe|sequenze]], definita come la frazione di posizioni differenti osservate in un [[Allineamento di sequenze pairwise|allineamento]] tra due stringhe $s_i$ e $s_j$. Essa quantifica direttamente la divergenza apparente contando mismatch e, a seconda della convenzione adottata, anche posizioni contenenti gap.

Formalmente, la p-distance è definita come:$$
f_{i,j}=\frac{\text{numero di siti differenti}}{\text{lunghezza dell’allineamento}}
$$Nel caso in cui le sequenze abbiano la stessa lunghezza e non siano presenti gap, la **proportional distance** coincide con la versione normalizzata della [[Hamming distance]]:$$
f_{i,j}=\frac{H(s_i,s_j)}{n}
$$dove $H(s_i,s_j)$ è la distanza di Hamming e $n$ la lunghezza comune delle sequenze
![[IMG - esempio di due stringhe con differenze.png]]


