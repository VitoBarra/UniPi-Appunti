---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Data analisys - Clustering
---
il __clustering__ è il processi di ricerca di sotto partizioni di dati che sono più simili tra loro.

l obiettivo è trovare un raggruppamento naturale per i dati ovvero trovare dei _cluster_
![[C1983390-D9A8-4A16-B97F-34946F5F67C1.jpeg]]
i dati in un cluster si organizzano attorno ad un _centroide_ ovvero un punto medio tra tutti i punti di quel __cluster__



### Clustering tramite quantizzazione di vettori
un modo di fare __clustering__ tramite l utilizzo di [[Quantizzatori Vettoriali (VQ)]] 

si cercare dei [[Partizione di un insieme|partizionamenti]] __ottimi__ di una [[Distribuzione di probabilita|distribuzione]] $p$ di input sconosciuta in regioni  dette __cluster__ approssimate da un __centroide__. 
Ovvero si sta cercando un [[Insiemi Matematici|insieme]] di vettori $\mathbf{w}_i \in c(x)$ che [[Quantizzatori Vettoriali (VQ)|quantizzano]] lo spazio in modo da minimizzare un certo errore di distorsione $d$ . 

Per trovare l insieme ottimo $c(x)$ possiamo formulare il problema come [[Problemi di minimizazione e massimizazione|problema di minimizzazione]]:
__sia__ l errore di distorsione $d\left(\mathbf{x}_i, \mathbf{c}(\mathbf{x}_j)\right) = \left\| \mathbf{x}_i - \mathbf{c}(\mathbf{x}_i) \right\|_2^2$  ovvero la [[Norme Matriciali e Norme Vettoriali|distantanza euclide]]
__allora__ possiamo definire una __funzione di loss__ come il [[Variabili aleatoria - Momenti|valore atteso]] dell errore di distorsione  $$
E = \int ( d\left( \mathbf{x}, c(\mathbf{x}) \right)  p(\mathbf{x}) \, d\mathbf{x} 
= \int \left\| \mathbf{x} - \mathbf{w}_{i^*(\mathbf{x})} \right\|^2_2 p(\mathbf{x}) \, d\mathbf{x}
$$dove $i^*(\boldsymbol x)= \arg_i \min \|\boldsymbol x -c_i(\mathbf{x})\|^2_2$  e quindi $\mathbf{w}_{i^*(\mathbf{x})}$ è il vettore di riferimento (__centroide__) a cui l input $\mathbf{x}$ è associato e $p(\mathbf{x})$ è la [[Definizione di Probabilita|probablità]] che l input sia $\mathbf{x}$.

Fissando 
- un insieme finito di input di cardinalità  $\ell$ 
- il numero di vettori di riferimento (__centroidi__) $K$
possiamo discretizare la precedente formula ottenendo:$$
E = \sum_{i}^{\ell} \sum_{j}^{K} \left\| \mathbf{x}_i - \mathbf{w}_j \right\|^2 \delta_{\text{winner}}(i,j)
$$Dove $$\delta_{\text{winner}}(i,j)= \begin{cases}
1  &  if  &  \mathbf{w_j} = w_{j^*(x_i)}   \\
 0& else 
\end{cases}$$si può trovare l insieme $c(x)$ ottimo minimizzando la funzione di loss