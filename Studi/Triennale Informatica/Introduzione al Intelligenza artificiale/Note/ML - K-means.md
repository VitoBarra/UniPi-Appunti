---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---
# K-means algoritmo ML
---
un algoritmo _non supervisionato_ per il [[Machine Learning|Machine Learning]]

si lavora con dati $<\boldsymbol x>$ senza lable
l obiettivo è trovare un raggruppamento naturale per i dati ovvero trovare dei _cluster_
![[C1983390-D9A8-4A16-B97F-34946F5F67C1.jpeg]]
_cluster_: sotto partizioni di dati simili tra loro.

i dati in un cluster si organizzano attorno ad un _centroide_ ovvero un punto medio tra tutti i punti di quel _cluster_


### Algoritmo
_Goal_: cercare dei partizionamenti ottimi di una distribuzione sono sicura in $\boldsymbol x$-space in regioni (cluster)  approssimato ad un _centroide_
- spazoni delle ipotesi $H$: un [[Insiemi Matematici|insieme]] di [[Quantizatori Vettoriali|quantizatori vettoriali]]  $x \rightarrow c(x)$ 
	- si passa da uno spazio continuo ad uno discreto
	- _Loss_$$L(h(\boldsymbol x_p))=\|\boldsymbol x_p-c(\boldsymbol x_p)\|^2$$
1. scegli $k$ _centroidi_ come $k$ punti selezionati a caso
2.  assegna ad ogni data point il cluster più vicino
3. sposta il centroide utilizzando la classificazione del passo 2.
4. se un _criterio di convergenza_ non è soddisfatto ritorna al passo __2.__


#### dettagli
- Dato i centroidi $c_1,\dots,c_K$ vettori di dimension $n$ (dimension degli input)
- per ogni dato $\boldsymbol x$ il cluster vincente è
	- $$i^*(\boldsymbol x)= \arg_i \min \|\boldsymbol x -c_i\|^2_2$$
- per ogni cluster $i$ il nuovo _centroide_ è
	- $$c_i=\frac{1}{|cluster_i|}\sum_{j:x_j\in cluster_i}\boldsymbol x_j$$
>[!example]- visual rapresentation 
>![[53FD956D-E338-4DDF-923B-FDF28C4F01B7.gif]]


### Limitazioni
- deve essere _conosciuti a priori_ il numero di cluster
	- si prova con try and error
- _loss_ con minimi locali che dipendono
	- risultati che dipendono dal inizializzazione
- funziona bene solo per _cluster_ ipersferici
	- per forme diverse non funziona 
	- ![[E461230C-BFBE-420F-A3B6-DBE774395364.jpeg]]
- non ci permette di proiettare i dati in una _dimensione più bassa_

##### Riduzione 
_riduzione di dimensione_: 
- $<x_1,x_2,\dots,x_n> \rightarrow <x_1’,\dots,x’_{n’}>$ con $n>n’$
- dove le nuove feature possono essere una combinazione delle originali.

