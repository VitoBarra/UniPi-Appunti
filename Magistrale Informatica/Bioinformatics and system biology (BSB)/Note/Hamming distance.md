---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Hamming distance
---
La **Hamming distance** è una [[Definizione di distanza|distanza]] nello spazio delle [[stringhe|stringhe]] usata per fare il  [[Confronto tra sequenze| confronto tra stirnghe]] di **uguale lunghezza**. Questa è definita come il **numero di posizioni** in cui i simboli corrispondenti sono diversi. Formalmente, date due [[Stringhe|stringhe]] $X$ e $Y$ di lunghezza $n$, la **Hamming distance** è definita come il numero di indici $i$ tali che $X_i \neq Y_i$. La misura è quindi applicabile solo a stringhe della stessa lunghezza e non ammette operazioni di inserzione o cancellazione.

La Hamming distance può essere interpretata come un caso particolare di [[edit distance|edit distance ]]confronto tra stringhe in cui:
- l’unica operazione consentita è la **sostituzione**,
- non sono ammessi **gap**,
- tutte le posizioni contribuiscono in modo indipendente al risultato finale.
ad esempio nel immagine i simboli diversi sono 5 quindi l'hammin distance è 5
![[IMG - esempio di due stringhe con differenze.png]]
