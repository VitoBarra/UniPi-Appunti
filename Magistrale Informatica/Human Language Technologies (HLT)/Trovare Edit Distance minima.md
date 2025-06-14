---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Trovare Edit Distance minima
---
per trovare l [[Edit distance|edit minima]], cerchiamo un percorso (una sequenza di modifiche) dalla stringa di partenza a quella finale:

- **Stato iniziale**: la parola che stiamo trasformando
- **Operatori**: inserimento, cancellazione, sostituzione
- **Stato obiettivo**: la parola che vogliamo ottenere
- **Costo del percorso**: ciò che vogliamo minimizzare, ovvero il numero di modifiche

![[Edit distance es 2.png]]

Tuttavia, lo spazio di tutte le possibili sequenze di modifiche è enorme. Non possiamo permetterci di esplorarlo in modo ingenuo, poiché molti percorsi distinti finiscono per raggiungere lo stesso stato. Non è necessario tener traccia di tutti questi percorsi, ma solo del più corto verso ciascuno degli stati modificati.

Possiamo definire la **distanza di edit minima** per due stringhe X e Y di lunghezza rispettivamente _n_ e _m_. Definiamo **D(i, j)** come la distanza di edit tra i primi _i_ caratteri di X e i primi _j_ caratteri di Y, cioè tra $X[1\dots i]$ e $Y[1\dots j]$. La distanza di edit tra X e Y sarà quindi **D(n, m)**.

Si usa un algoritmo di [[Programmazione Dinamica]] che fornisce un metodo tabellare per calcolare $D(n, m)$ e risolve il problema combinando soluzioni a sotto problemi.

**Bottom-up**:

- Calcoliamo D(i, j) per valori piccoli di i e j
- E poi usiamo questi per calcolare valori più grandi di D(i, j)
- Ossia, calcoliamo D(i, j) per tutti gli i (0 < i < n) e j (0 < j < m)


![[Edit distance algoritmo.png]]