---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Analisi Filogenetica - Metodo su distanza UPGMA
---
**UPGMA** (*Unweighted Pair Group Method with Arithmetic Mean*) è un [[Analisi filogenetica - Metodi basati su distanza|metodo basato su distanza]] per l’[[Analisi filogenetica|analisi filogenetica]]. Esso utilizza un approccio di **clustering gerarchico agglomerativo** per costruire un **albero filogenetico** a partire da una matrice di distanze pairwise tra sequenze.

L’idea centrale dell’algoritmo è che le sequenze più simili vengano raggruppate per prime, formando cluster progressivamente più grandi. Ogni fusione tra cluster corrisponde alla creazione di un nuovo nodo interno dell’albero, fino a ottenere un’unica struttura che include tutte le sequenze.

L’algoritmo può essere descritto dai seguenti passi fondamentali:

- ogni sequenza viene inizialmente considerata come un cluster singolo $C_i$;
- si calcola una matrice di distanze $D(i,j)$ tra tutti i cluster (inizialmente tra tutte le coppie di sequenze);
- ogni cluster è rappresentato come una foglia dell’albero posta a quota $0$;
- finché esistono più cluster distinti:
	- si selezionano i due cluster $i$ e $j$ con distanza minima $D(i,j)$;
	- questi cluster vengono uniti in un nuovo cluster $k=i\cup j$;
	- si introduce un nodo padre comune a quota:
	$$
	h(k)=\frac{D(i,j)}{2}
	$$
	- la distanza tra il nuovo cluster $k$ e ogni altro cluster $r$ viene aggiornata come media aritmetica:
	$$
	D(k,r)=\frac{|C_i|\,D(i,r)+|C_j|\,D(j,r)}{|C_i|+|C_j|}
	$$
	dove $|C_i|$ e $|C_j|$ sono le cardinalità dei cluster.

![[IMG - UPGMA esempio animazione 1.gif]]

La regola di aggiornamento delle distanze riflette il carattere *unweighted* dell’algoritmo, poiché le distanze tra cluster vengono ottenute come medie delle distanze tra le sequenze contenute nei gruppi, senza introdurre modelli evolutivi più complessi.

UPGMA produce alberi in cui tutte le foglie risultano allo stesso livello, cioè alberi **ultrametrici**. Una matrice di distanze è detta **ultrametrica** se per ogni tripla di sequenze $(a,b,c)$ vale la proprietà:
$$
D(a,b)\leq \max\{D(a,c),D(b,c)\}
$$
equivalentemente, i due valori maggiori tra le tre distanze sono sempre uguali. Questa condizione implica che tutte le sequenze si siano evolute con lo stesso tasso, secondo l’ipotesi di **molecular clock**.

Di conseguenza, UPGMA funziona correttamente solo quando le distanze soddisfano la proprietà di ultrametricità; in caso contrario, l’albero risultante può presentare lunghezze dei rami e topologie distorte.

![[IMG - UPGMA distanze degli archi.png]]

