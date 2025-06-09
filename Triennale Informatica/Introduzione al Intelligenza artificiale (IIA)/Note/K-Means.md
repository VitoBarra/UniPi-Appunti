---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---
# K-Means
---
il __$k$-Means__ è un [[Algoritmi di learning NON supervisionato|algoritmo di apprendimento non supervisionato]] [[Modelli Instance-Based|Instance-Based]]  usat[[Data analysis -  Clustering|clustering]]stering]] 


Un modo di fare __clustering__ è tramite l'utilizzo di [[Quantizzatori Vettoriali (VQ)]]. 

Si cercano dei [[Partizione di un insieme|partizionamenti]] __ottimi__ di una [[Distribuzione di probabilita|distribuzione]] $p$ di input sconosciuta in regioni, dette __cluster__, approssimate da un __centroide__. 
Ovvero si sta cercando un [[Insiemi Matematici|insieme]] di vettori $\mathbf{w}_i \in c(x)$ che [[Quantizzatori Vettoriali (VQ)|quantizzano]] lo spazio in modo da minimizzare un certo errore di distorsione $d$ . 

Per trovare l'insieme ottimo $c(x)$ possiamo formulare il problema come [[Problemi di ottimizzazione|problema di minimizzazione]]:
__sia__ l'errore di distorsione $d\left(\mathbf{x}_i, \mathbf{c}(\mathbf{x}_j)\right) = \left\| \mathbf{x}_i - \mathbf{c}(\mathbf{x}_i) \right\|_2^2$,  ovvero la [[Norme Matriciali e Norme Vettoriali|distanza euclidea]],
__allora__ possiamo definire una __funzione di loss__ come il [[Variabili aleatoria - Momenti|valore atteso]] dell errore di distorsione  $$
E = \int ( d\left( \mathbf{x}, c(\mathbf{x}) \right)  p(\mathbf{x}) \, d\mathbf{x} 
= \int \left\| \mathbf{x} - \mathbf{w}_{i^*(\mathbf{x})} \right\|^2_2 p(\mathbf{x}) \, d\mathbf{x}
$$dove $i^*(\boldsymbol x)= \arg_i \min \|\boldsymbol x -c_i(\mathbf{x})\|^2_2$  e quindi $\mathbf{w}_{i^*(\mathbf{x})}$ è il vettore di riferimento (__centroide__) a cui l'input $\mathbf{x}$ è associato e $p(\mathbf{x})$ è la [[Definizione di Probabilita|probabilità]] che l'input sia $\mathbf{x}$.

Fissando :
- un insieme finito di input di cardinalità  $\ell$ 
- il numero di vettori di riferimento (__centroidi__) $K$
possiamo discretizzare la precedente formula ottenendo:$$
E = \sum_{i}^{\ell} \sum_{j}^{K} \left\| \mathbf{x}_i - \mathbf{w}_j \right\|^2 \delta_{\text{winner}}(i,j)
$$Dove $$\delta_{\text{winner}}(i,j)= \begin{cases}
1  &  if  &  \mathbf{w_j} = w_{j^*(x_i)}   \\
 0& else 
\end{cases}$$Si può trovare l'insieme $c(x)$ ottimo minimizzando la funzione di [[Data analysis -  Clustering|clustering]] usa l approccio che utilizza la [[Quantizzatori Vettoriali (VQ)|quantizazione vettorialie]].
[[Derivate|Derivando]] la funzione di loss si ottiene la regola di aggiornamento: $$\Delta \mathbf{w}_{i^*} = \eta \delta_{winner} (i,i^*)(x_i-w_{i^*}) $$ e questa regola costituisce la versione __[[Tecnica di ottimizzazione Gradient Descent|online]]__ del __$k$-mean__

Mentre la versione __[[Tecnica di ottimizzazione Gradient Descent|batch]]__ segue come:
1. Scegliere $k$ __centroidi__ iniziali, posizionandoli in uno dei seguenti modi:
    - Selezionando casualmente $k$ punti dal set di dati.
    - Definendo $k$ punti casuali all'interno dell'iper-volume che contiene il set di dati.
2. Assegnare ogni punto del dataset al __centroide__ più vicino (ovvero al cluster più vicino).
3. Ricalcolare i __centroidi__ dei cluster come la media geometrica dei punti attualmente assegnati a ciascun cluster.
	- per ogni $cluster_i= \{x \in TR \mid d(x,w_i)\leq d(x,w_j) \ \forall j \}$  il nuovo _centroide_ $$\mathbf{w}_i=\frac{1}{|cluster_i|}\sum_{\mathbf{x}_j\in cluster_i}\mathbf{x}_j$$ dove $|cluster_i|$ è il numero di elementi nel cluster
	    
4. Se il criterio di convergenza non è soddisfatto, tornare al passo $2$. Alcuni possibili criteri di convergenza sono:
    - Nessuna (o minima) riassegnazione di punti ai cluster.
    - Minima riduzione dell'errore quadratico.

Ripetere il processo fino al raggiungimento della convergenza.


![[53FD956D-E338-4DDF-923B-FDF28C4F01B7.gif]]


### Discussione
il __$k$-means__ è un algoritmo molto semplice ma si devono conoscere a priori il numero di cluster $k$ che ci vogliono cercare il che può comportare il trovare il numero giusto tramite try and error.
è un problema di ottimizzazione locale quindi soffre del problema dei __minimi locali__ e quindi la soluzione dipende dal punti di inizio. Funziona bene solo nei casi in cui i dati siano in uno ipersfera compatta e non funziona quindi bene con forme diverse dei dati ad esempio con forme concave. ![[E461230C-BFBE-420F-A3B6-DBE774395364.jpeg]]
in più questo algoritmo __non__ ci permette di proiettare i dati in una __dimensione più bassa__.


