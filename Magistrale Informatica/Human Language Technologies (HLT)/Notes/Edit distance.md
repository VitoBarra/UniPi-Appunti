---
Course: "[[Human Language Technology (HLT)]]"
Course 2:
tags:
  - HLT
  - BSB
Area:
topic:
SubTopic:
---
# Edit distance
---
L’**Edit Distance** è una [[Definizione di distanza|distanza]] nello spazio delle [[Stringhe|stringhe]] che quantifica **quanto sono simili due [[Stringhe|stringhe]]** $X$ ed $Y$ ed è quindi usata anche per [[Confronto tra sequenze|confrontarle]]. Questa è definita come il **costo minimo della sequenza di operazioni di edit** necessarie per trasformarne $X$ in $Y$. 
Le operazioni di **edit** ammesse sono:
- **Inserzione** di un carattere
- **Cancellazione** di un carattere
- **Sostituzione** di un carattere con un altro
e ogni operazione può essere associata a un **costo specifico** dove  se tutte le operazioni hanno costo **1**, si ottiene la **distanza standard** mentre se le operazioni hanno **costi differenti**, la distanza riflette una nozione di similarità più articolata. Una variante particolarmente nota è la **distanza di Levenshtein**, in cui la sostituzione ha un costo maggiore rispetto all’inserzione e alla cancellazione. La scelta dei costi determina il tipo di trasformazioni considerate più o meno penalizzanti.

il calcolo dell’**edit distance** può essere interpretato come la costruzione di un **[[Allineamento di sequenze|allineamento]]** tra due [[Stringhe|stringhe]]. A ciascun carattere di una stringa viene associato un carattere dell’altra stringa oppure un’operazione di inserzione o cancellazione.
![[IMG - esempio Edit distance.png]]

Nel quadro dei [[Analisi di sequenze]], l’edit distance costituisce una misura generale e indipendente dal dominio, che fornisce un criterio astratto di confronto su cui si basano tecniche più specifiche di [[Allineamento di sequenze|allineamento]] e analisi delle sequenze. 

L’edit distance è ampiamente utilizzata nel [[Natural Language Processing]] per confrontare parole o frasi in base alla loro similarità formale. Essa viene impiegata in compiti quali la correzione ortografica, il riconoscimento di entità, la valutazione di modelli di traduzione automatica e il rilevamento di plagio.


