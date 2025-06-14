---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Distanza di Jukes-Cantor
---
La **distanza di Jukes–Cantor** è una **[[Definizione di distanza|distanza]] evolutiva** utilizzata nell’[[Analisi filogenetica]] per stimare la divergenza tra due [[Stringhe|sequenze]] biologiche, correggendo il fatto che uno stesso sito può aver subito più eventi di sostituzione nel corso del tempo. Essa rappresenta un modello specifico per sequenze nucleotidiche e costituisce una delle correzioni più semplici della [[Proportional distance (p-distance)|proportional distance]], poiché introduce un aggiustamento per tenere conto di sostituzioni multiple che non risultano direttamente osservabili nell’allineamento.

Il modello di Jukes–Cantor si basa su ipotesi fortemente simmetriche sul processo evolutivo. In particolare assume che le quattro basi [[Nucleotidi|nucleotidiche]] compaiano con [[Probabilita con distribuzione uniforme|frequenza uniforme]], pari a $\mathcal{P}=1/4$ ciascuna, e che tutte le sostituzioni possibili tra basi avvengano con lo stesso tasso, senza distinzione tra transizioni e trasversioni. Inoltre, ogni sito della sequenza evolve indipendentemente dagli altri secondo un [[Markov chains|processo di Markov continuo nel tempo]], con un tasso costante di cambiamento.

In queste condizioni, la distanza evolutiva viene interpretata come il [[Variabili aleatoria - Momenti|numero medio atteso]] di mutazioni accumulate per sito. Formalmente, la **distanza di Jukes–Cantor** è definita come:$$
d_{i,j}=-\frac{3}{4}\ln\left(1-\frac{4}{3}p\right)
$$dove $p$ rappresenta la frazione osservata di siti differenti tra due sequenze, ossia la [[Proportional distance (p-distance)|p-distance]].  

Per valori piccoli di $p$, la distanza corretta rimane vicina alla distanza osservata, mentre per sequenze più divergenti la correzione diventa significativa. All’aumentare della divergenza, la funzione [[Funzione logaritmica|logaritmica]] cresce più rapidamente, riflettendo l’accumulo di sostituzioni multiple che non possono essere rilevate direttamente dal semplice conteggio dei mismatch.
