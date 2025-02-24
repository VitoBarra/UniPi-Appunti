---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Gradient Descent
---
Il __Gradient descent__ è una __tecnica di ottimizzazione__ che sfrutta il [[Funzioni Multivariata - Gradiente|gradiente]] di una funzione detta __funzione di loss__ per minimizzarla. 
Ovvero si aggiornano i valori su ciò è calcolata la Loss seguendo la direzione di decrescita del gradiente.



Per fare __gradient descent__ Esistono tre approcci principali che variano per come gestiscono l'insieme di  $n$ pattern da utilizzare durante l' [[Algoritmi di Machine Learning|algoritmo di learning]]:

1. __Batch__: In questo approccio si utilizza l'intero dataset per calcolare la discesa del gradiente. Questo metodo garantisce uno spostamento molto stabile verso un minimo, poiché il gradiente viene calcolato considerando tutti i pattern disponibili. Tuttavia, l'elaborazione risulta più lenta e può essere computazionalmente onerosa per dataset di grandi dimensioni.
2. __Mini-batch__ (__stocastic gradient descent__): Questo approccio rappresenta un compromesso tra batch e online. I dati vengono suddivisi in piccoli sottoinsiemi (detti __mini-batch__), e il gradiente viene calcolato per ciascun sottoinsieme. Questo metodo combina la stabilità del batch con una maggiore velocità e una riduzione del costo computazionale rispetto all'elaborazione dell'intero dataset.
   ![[Pasted image 20250111104614.png]]

3. __Online__: Qui il gradiente viene ricalcolato a ogni nuovo pattern $p$, dando vita alla cosiddetta discesa di gradiente __stocastica__. Questo approccio è generalmente il più veloce, ma per garantire stabilità richiede l'adozione di passi di apprendimento $\eta$ più piccoli. Inoltre, può essere soggetto a maggiore instabilità a causa della variabilità introdotta da singoli pattern.

Ogni metodo ha i suoi punti di forza: __il batch__ garantisce stabilità, __il mini-batch__ offre un buon equilibrio tra stabilità e velocità, mentre __l'online__ privilegia la velocità, ma può essere meno stabile.
![[Pasted image 20250111101827.png]]
	  
