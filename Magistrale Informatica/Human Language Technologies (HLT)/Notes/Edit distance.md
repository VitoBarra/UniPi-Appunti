---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Edit distance
---
L’**Edit Distance** è una misura che quantifica **quanto sono simili due stringhe**, contando il **numero minimo di operazioni** necessarie per trasformarne una nell’altra.

Le operazioni ammesse sono:

- **Inserzione** di un carattere
- **Cancellazione** di un carattere
- **Sostituzione** di un carattere con un altro

Questa misura è ampiamente usata nel [[Natural Language Processing]] per confrontare parole o frasi in base alla loro similarità. questo viene di solito usato per i task di correzione ortografica, riconoscimento di entità, valutazione di modelli di traduzione automatica e rilevamento di plagio.

Per calcolare l’edit distance tra due stringhe, si crea un **allineamento** tra i caratteri. Ad esempio, tra le parole:
$\text{intention}$
$\text{execution}$

si stabilisce una corrispondenza tra sottostringhe, e sotto ogni carattere si annota il tipo di operazione effettuata:
- `d` per cancellazione (delete),
- `i` per inserzione (insert),
- `s` per sostituzione (substitute).

![[Edit distance es 1.png]]
Ogni operazione può avere un costo specifico:

- Se tutte le operazioni valgono **1**, otteniamo la **distanza standard**.
- Se la sostituzione vale **2** (come nel caso della **distanza di Levenshtein**), il risultato cambia.

## Algorithm

IPer trovare la distanza di edit minima, cerchiamo un percorso (una sequenza di modifiche) dalla stringa di partenza a quella finale:

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